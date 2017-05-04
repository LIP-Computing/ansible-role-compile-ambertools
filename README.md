# ansible-role-compile-ambertools

Ansible role to compile ambertools and produce a binary tarball

## Compile using a docker container

Run a docker with mounting a volume that will have the binary tarball
The compilation will be dane manually for now

```
mkdir ambertar
export MDIR=`pwd`/ambertar
docker run -it -v /home:$MDIR -w /home lipcomputing/ansible-ubuntu16.04 /bin/bash
ansible-galaxy install git+https://github.com/LIP-Computing/ansible-role-compile-ambertools.git
ansible-playbook /etc/ansible/roles/ansible-role-compile-ambertools/tests/ambertools.yml
export AMBERHOME=/home/amber16
cd /home/amber16
./configure --with-python /usr/bin/python -mpi -noX11 gnu
make install
rm -rf config.h configure logs src test
mv AmberTools /home/
mv dat /home/AmberTools/ 
cd ../
tar zcvf amber17-bin-ubuntu16.04.tgz amber16
tar zcvf amber17-examples-ubuntu16.04.tgz AmberTools
```
