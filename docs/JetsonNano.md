# Installation du JetPack

Toutes les informations liées à l'installation du jetpack sont ici : https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-2gb-devkit

# Installation des outils pour utiliser le projet "jetson-inference"

Toutes les informations liées au projet sont ici : https://github.com/dusty-nv/jetson-inference

Résumé des commandes à effectuer :

``` bash
$ sudo apt-get update
$ sudo apt-get install git cmake
$ git clone https://github.com/dusty-nv/jetson-inference
$ cd jetson-inference
$ git submodule update --init
$ sudo apt-get install libpython3-dev python3-numpy
$ mkdir build
$ cd build
$ cmake ../
$ make
$ sudo make install
$ sudo ldconfig
```

Le menu suivant s'affichera, appuyez sur la touche `espace` pour sélectionner les réseaux de neurones à télécharger. Appuyez sur `entrer` pour continuer.

<img src="images/download-models.jpg" width="650">

Si vous voulez relancer l'**outil de téléchargement de modèles** plus tard, utilisez la commande suivante :

``` bash
$ cd jetson-inference/tools
$ ./download-models.sh
```

Le menu suivant s'affichera, appuyez sur la touche `espace` pour sélectionner la version de PyTorch. Appuyez sur `entrer` pour continuer.

<img src="images/pytorch-installer.jpg" width="650">

Si vous voulez relancer l'**outil d'installation de Pytorch** plus tard, utilisez la commande suivante :

``` bash
$ cd jetson-inference/build
$ ./install-pytorch.sh
```

# Installation de ROS Melodic

Toutes les informations liées à sont ici : http://wiki.ros.org/melodic/Installation/Ubuntu

Résumé des commandes à effectuer :

``` bash
$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
$ sudo apt install curl
$ curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
$ sudo apt update
$ sudo apt install ros-melodic-ros-base
$ echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
$ sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
$ sudo apt-get install python3-catkin-pkg-modules
$ sudo apt-get install python3-rospkg-modules
$ sudo rosdep init
$ rosdep update

$ sh -c "echo \"export ROS_MASTER_URI=http://localhost:11311\" >> ~/.bashrc"
$ sh -c "echo \"export ROS_HOSTNAME=localhost\" >> ~/.bashrc"
```

### Pour configurer ROS, il faut éditer  le fichier bashrc avec la commande suivante :
``` bash
$ nano ~/.bashrc
$ source ~/.bashrc
```
<img src="images/bashrc.PNG" width="650">

**ROS_MASTER_URI** : L'adresse IP de l'ordinateur qui lance le nœud ROS master

**ROS_HOSTNAME** : L'adresse IP du Jetson Nano