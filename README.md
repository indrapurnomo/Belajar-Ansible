# Belajar-Ansible
Test ansible roles using molecule and deploy to digital ocean

# Molecule
Create and testing ansible role using Molecule and serverspec

## Dependency
* virtualbox
* vagrant
* python pip
* ansible
* serverspec (verifier)

## Install molecule-dep
```
$ apt-get update
$ apt-get install gcc python-pip python-vagrant libssl-dev libffi-dev
```

## Install Molecule using pip:
```
$ pip install ansible
$ pip install docker-py
$ pip install molecule
```

## How to use
`$ molecule --help` | to show others command  
`$ molecule init --role nginx --verifier serverspec` | create new rule from scratch using serverspec for verifier  
`$ bundle install`  

## Addition setup
We using debian jessie64, so please edit platform section in molecule.yml  
```
platforms:
    - name: debian/jessie64
      box: debian/jessie64
      box_url: https://vagrantcloud.com/debian/boxes/jessie64/versions/8.7.0/providers/virtualbox.box
```

## Testing
`$ molecule test --destroy=always` | start testing  
More about `serverspec` testing can be found at [serverspec.org](http://serverspec.org/resource_types.html)

## Debug  
`$ ssh ubuntu@127.0.0.1 -p 2222 -i $(pwd)/nginx/.vagrant/machines/nginx/virtualbox/private_key`

## Implement v1
hosts file need create manual, and make sure public key configured  
`$ ansible-playbook nginx/playbook.yml -i nginx/hosts --private-key ~/.ssh/id_rsa --user ubuntu`

## Implement v2
`$ ansible-playbook nginx/playbook.yml -i nginx/environment/staging --private-key ~/.ssh/id_rsa --user ubuntu`

## Documentations
* https://github.com/metacloud/molecule
* https://molecule.readthedocs.io

## Documentations video
* https://www.youtube.com/watch?v=H2YimybJmYk || Testing Ansible Roles menggunakan Molecule 
* https://www.youtube.com/watch?v=g37vgxzKC68 || Deploy ke server Digital Ocean dengan Ansible-Playbook 
