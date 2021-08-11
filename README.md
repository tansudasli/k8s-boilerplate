# k8s-boilerplate

Boilerplate for k8s cluster. In every product development, you are going to need infrastructure. 
In every architecture, there are common parts, and also many technical decisions have to be taken.

Every start-up have to manage costs while considering scalability.
Also, regarding product-idea requirements, some technical decisions such as storages, dbs, cloud vs on-premise etc...
<br>There are other things which are not obviously important at the beginning like managing learning-curve, technical debts, naming standards...

So, There are so many ways, and there is no perfect architecture, but we should try to put better approaches.

- Physical nodes (Min. 1)
  - preparations
  - bootstrapping  
  - k8s  
- Front-end layer (w/ ingress controller + services to load balance)
  - routing to static (www.)
  - routing to static (core., bo. or other micro-apps)
- Backend layer
  - Connections from (core.) 
- Storage layer (local disks or distributed storage)
- Data lake (on object storage)
- Data pipelines (distributed computing)
- ML pipelines
- Backups

## Strategy

## How to start

Install Ansible on you local machine, then

- Prepare physical nodes. 
  <br>Making this part automated is quite long topic. Such as, automate virtualbox w/ vagrant or automate virtualbox w/ multipass via
  leveraging cloud-init vs ansible, CLIs vs ansible cloud provider specific roles... It also depends on 
  infrastructure strategy like bare metals vs cloud providers (flavors like GKE are much sense instead of compute nodes).
  <br><br>
  
  - Manually create bare-metals (on your local machine using Virtualbox, or bare-metal-as-a-service provider (Scaleway) or 
    in your DC). So adjust basic networking things (i.e. on virtualbox use bridged network), and then
    - Complete `OS installation`
      - Set hostname as `base` 
      - Create `default user` as admin during installation
      - Create `ansible` user (as service account), add to `sudo` and `adm` groups, and your public-key
      - ssh-server  
      - Set static IP
    - Get `machine IPs`, and Update the `hosts` file.

    Steps in `OS installation` normally can be automized by `cloud-init`. To use cloud-init in Virtualbox, You need 
    - `multipass` or
    - `vagrant` or 
    -  manually run `cloud-init.yaml` on the machine. Check cloud-init.yaml for more!

- Bootstrapping.
  <br>Every server needs some checks, installations, or hardening etc...
    - Check virtualization
    - Set hostname as `hosts` file
    - Set networking (static IP)

- K8s

- Test