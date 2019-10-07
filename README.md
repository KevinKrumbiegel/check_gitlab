# check_gitlab
Nagios plugin for doing a GitLab health check.

** Usage: **

*** In Nagios: ***
1. Download the check_gitlab file. (i.e. using `wget -P ~/ https://github.com/KevinKrumbiegel/check_gitlab/blob/master/check_gitlab`)
2. Mark the file as executable (i.e. using `sudo chmod +x ~/check_gitlab`)
3. Move the file to /usr/lib/nagios/plugins/ (i.e. using `mv ~/check_gitlab /usr/lib/nagios/plugins/check_gitlab)
4. Optionally use the gitlab.conf file as a CheckCommand definition in icinga2 (by default all checks will be executed)

*** Standalone: ***
1. Download the check_gitlab file. (i.e. using `wget -P ~/ https://github.com/KevinKrumbiegel/check_gitlab/blob/master/check_gitlab`)
2. Execute the file (Python needs to be installed)

Copyright (c) 2019 Kevin Krumbiegel"

Usage: ./check_gitlab -s <server_url> [-h] [--cache-check] [--db-check] [--gitaly-check] [--queues-check] [--redis-check] [--shared-state-check]

-s <server_url>      = URL of the server to be checked. (i.e. https://gitlab.example.org/)
-h                   = This screen
Checks:")
--check-cache        = Enable checking cache status
--check-db           = Enable checking database status
--check-gitaly       = Enable checking gitaly status
--check-queues       = Enable checking queues status
--check-redis        = Enable checking redis status
--check-shared-state = Enable checking shared state status

** Background **
The check_gitlab script queries the JSON-API endpoint of a GitLab server using the "Liveness" feature.
By now it checks whether the status of all specified modules is "ok".
In case the status is not okay, a cricital condition will be reported.
If an exception occurs or the check is executed with bad parameter configuration, an unknown condition will be reported.

** Further information **

For further information see:
[GitLab web page](https://about.gitlab.com/)
[GitLab Health Check documentation](https://docs.gitlab.com/ee/user/admin_area/monitoring/health_check.html)
[Icinga](https://icinga.com/)