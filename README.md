# Exult-void-Linux
Exult is a project to recreate Ultima 7 for modern operating systems, using the game's original plot, data, and graphics files.</p>
This version is commiled for Linux void</p>

https://github.com/exult/exult

![Screenshot](https://github.com/johna23-lab/Exult-void-Linux/blob/main/exult.void.png?raw=true)

HOW TO COMPILE
sudo xbps-install automake libtool timidity libXft SDL2-devel libfluidsynth libmt32emu-devel -y
git clone https://github.com/exult/exult.git
wget http://downloads.sourceforge.net/exult/exult_audio.zip
cd exult
echo $(git rev-list --count master).$(git rev-parse --short master)
./autogen.sh
LIBS="-lXft -lX11" ./configure --prefix=/usr --enable-static-libraries --disable-shared
--with-timidity="/etc/timidity++/timidity.cfg" --enable-mt32emu
make
make install DESTDIR=/home/$USER/exult_c

CREATING THE XBPS PACKAGE WITH DEPENDENCIES
chmod -R 755 /home/$USER/exult_c/usr
xbps-create -q -A "x86_64" -n "exult_1.9-8253_1" -s "exult_1.9-8253 pkg" -D  "SDL2>=2.0.22 libmt32emu>=2.5.1
leafpad>=0.8.18.1 qpdfview>=0.4.18 timidity>=2.15.0" --compression xz exult_1.9

INSTALLING THE PACKAGE
xbps-rindex -a exult_1.9-8253_1.x86_64.xbps
sudo xbps-install -R $PWD exult_1.9-8253_1

THAT'S IT! now you need to download the game and PLAY IT!!
