# Exult-void/ubuntu/mint/..Linux
Exult is a project to recreate Ultima 7 for modern operating systems, using the game's original plot, data, and graphics files.</p>
This version is compiled for Linux void</p>

https://github.com/exult/exult

![Screenshot](https://github.com/johna23-lab/Exult-void-Linux/blob/main/exult.void.png?raw=true)

<b>HOW TO COMPILE</b></br>
sudo xbps-install automake libtool timidity libXft SDL2-devel libfluidsynth libmt32emu-devel -y</br>
git clone https://github.com/exult/exult.git</br>
cd exult</br>
echo $(git rev-list --count master).$(git rev-parse --short master)</br>
./autogen.sh</br>
wget https://www.libsdl.org/tmp/release/SDL2-2.0.22.tar.gz</br>
tar xvfa SL2-2.0.22.tar.gz</br>
cd SL2-2.0.22</br>
./configure --enable-static --disable-shared --prefix=$PWD</br>
make -j4</br>
cd ..</br>
LIBS="-lXft -lX11" ./configure --prefix=/usr --enable-static-libraries --disable-shared</br>
make</br>
make install DESTDIR=/home/$USER/exult_c</p></p>

<b>CREATING THE XBPS PACKAGE WITH DEPENDENCIES</b></br>
chmod -R 755 /home/$USER/exult_c/usr</br>
xbps-create -q -A "x86_64" -n "exult_1.9-8253_1" -s "exult_1.9-8253 pkg" -D --compression xz exult_c</p></p>

<b>INSTALLING THE PACKAGE</b></br>
xbps-rindex -a exult_1.9-8253_1.x86_64.xbps</br>
sudo xbps-install -R $PWD exult_1.9-8253_1</p>

THAT'S IT! now you need to download the game and PLAY IT!!</p>
