# Rollback Demo

Test out automatic snap rollbacks. Install the good version:

    $ sudo snap install --beta rollback-demo-kyrofa

Verify that it's the good version:

    $ snap list
    Name                  Version                   Rev   Developer      Notes
    core                  16-2                      1441  canonical      -
    rollback-demo-kyrofa  0.1.0                     1     kyrofa         -

    $ rollback-demo-kyrofa.test 
    I'm the good version

Now refresh to the broken version:

    $ sudo snap refresh --edge rollback-demo-kyrofa
    error: cannot perform the following tasks:
    - Run configure hook of "rollback-demo-kyrofa" snap if present (run hook "configure": This version of the snap is broken!)

Verify that the snap rolled back to the good version again:

    $ snap list
    Name                  Version                   Rev   Developer      Notes
    core                  16-2                      1441  canonical      -
    rollback-demo-kyrofa  0.1.0                     1     kyrofa         -

    $ rollback-demo-kyrofa.test
    I'm the good version
