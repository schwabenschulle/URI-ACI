**How to play**

ansible-playbook play__static-routes.yml -i ../ansible-aci-inventory/MY-INVENTORY

See run example output at the end

**Play-Book**

**Action of playbook**
- Promp for username and Password
- loop over list in inventory with fabrics and call role login_to_aci. Input is a list of hostname output a dict in list. Hostname/ip + Token. Can be 1 or N Fabrics
- loop over output of login_to_aci role and call role__static-routes-aci. 


**role__static-routes-aci**
It render the URI body in Jinja and save file an ansible-aci-play directory for verifcation and 
e.g. see route_uri_body_lab-fabric1.lab.net.json



**Run Example**
(aci) myuser@myhost:~/ansible/URI-ACI/ansible-aci-play$ ansible-playbook play__static-routes.yml -i ../ansible-aci-inventory/MY-INVENTORY
 [WARNING] Ansible is in a world writable directory (/home/rcf8fe/ansible/URI-ACI/ansible-aci-play), ignoring it as an ansible.cfg source.
 [WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'

What is your username?: admin
What is your password?:

PLAY [Configure static route in ACI] ******************************************************************************************************************************************************************************

TASK [login] ******************************************************************************************************************************************************************************************************

TASK [login_to_aci : Login ACI] ***********************************************************************************************************************************************************************************
ok: [localhost]

TASK [login_to_aci : set_fabric_array] ****************************************************************************************************************************************************************************
ok: [localhost]

TASK [login_to_aci : Login ACI] ***********************************************************************************************************************************************************************************
ok: [localhost]

TASK [login_to_aci : set_fabric_array] ****************************************************************************************************************************************************************************
ok: [localhost]

TASK [debug] ******************************************************************************************************************************************************************************************************
ok: [localhost] => {
    "fabric_array": [
        {
            "cookie": "APIC-cookie=FE4cAAAAAAAAAAAAAAAAADLjQ7VGW4eL1ey5+CHqVycclGvJsK9RPzeio1GVvZ6veHxz+jhV0LAXI1qw8psLfhi9N/N9rwrEC9dbqKLaE3XLJ5eQ58ATjzWUTuu7c4SvTdAqAdwYYgR94L6gdoL9GGwZnLCPbO7EXZ0K2UNSgv1FMA7qPEz2TplliW05xZFZtS0aCaMkft4gIGuyDDc1MQ==; path=/; HttpOnly; HttpOnly; Secure",
            "ip": "lab-fabric1.lab.net"
        },
        {
            "cookie": "APIC-cookie=ga4AAAAAAAAAAAAAAAAAAAde07dmxddCyd6Uj1pz2+jPNWuWjYEgF9wOOI4pizUr659zrfUXKGrQuPwEQDwmUmtEvcwpc6ev5fUOVMFMcYS+lJkZOSw6UptTiwqAEqbgpf1bw65AUVZ2l+QY3vZ5ur23isoefZ0rAt7wZWprOmmz6dt2FGuwrx6zEc3kc5bwf+VHDtpLHU08+67qwu/7Sw==; path=/; HttpOnly; HttpOnly; Secure",
            "ip": "lab-fabric2.lab.net"
        }
    ]
}

TASK [add routes in aci] ******************************************************************************************************************************************************************************************

TASK [role__static-routes-aci : create-body-file-for troubleshooting] *********************************************************************************************************************************************
ok: [localhost]

TASK [role__static-routes-aci : Add static route] *****************************************************************************************************************************************************************
ok: [localhost]

TASK [role__static-routes-aci : Display Error Message when deployment failed] *************************************************************************************************************************************
skipping: [localhost]

TASK [role__static-routes-aci : create-body-file-for troubleshooting] *********************************************************************************************************************************************
ok: [localhost]

TASK [role__static-routes-aci : Add static route] *****************************************************************************************************************************************************************
ok: [localhost]

TASK [role__static-routes-aci : Display Error Message when deployment failed] *************************************************************************************************************************************
skipping: [localhost]

PLAY RECAP ********************************************************************************************************************************************************************************************************
localhost                  : ok=9    changed=0    unreachable=0    failed=0

(aci) rcf8fe@FE-Z1TNY:~/ansible/URI-ACI/ansible-aci-play$