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
mv amber16 /usr/local/
export AMBERHOME=/usr/local/amber16
cd $AMBERHOME
./configure --with-python /usr/bin/python -noX11 gnu
make install
./configure --with-python /usr/bin/python -mpi -noX11 gnu
make install
rm -rf config.h configure logs src test
mv AmberTools /home/
mv dat /home/AmberTools/
cd ../
mv amber16 /home/
cd /home
tar zcvf amber17-bin-nompi-ubuntu16.04.tgz amber16-nompi
tar zcvf amber17-bin-mpi-ubuntu16.04.tgz amber16-mpi
tar zcvf amber17-examples-ubuntu16.04.tgz AmberTools
```
