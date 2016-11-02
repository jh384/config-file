# config-file
jimmyserver config file

define host {
        use                             linux-server
        host_name                       jimmyserver
        alias                           JHAll
        address                         127.0.0.1
        max_check_attempts              5
        check_period                    24x7
        notification_interval           30
        notification_period             24x7
}
define service {
        use                             generic-service
        host_name                       jimmyserver
        service_description             PING
        check_command                   check_ping!100.0,20%!500.0,60%
}
define service {
        use                             generic-service
        host_name                       jimmyserver
        service_description             SSH
        check_command                   check_ssh
        notifications_enabled           0
}
define service{
        use                             generic-service
        host_name                       jimmyserver
        service_description             Disk Space
        check_command                   check_local_disk!20%!10%!/
}
