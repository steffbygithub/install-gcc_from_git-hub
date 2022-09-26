# install-gcc_from_git-hub
Hier die Informationen zur Installation eines GCC Umfelds aus den Quellen über das Clonen des Remote-Repositories bei GNU-C/C++
# Disclaimer: 
Ich dokumentiere hier mein Vorgehen, um den Studierenden eine einheitliche cygwin-Umgebung zu gewährleisten. Benutzung auf eigene Gefahr!


# Source Code-Repository herunterladen und aktuelles Release auschecken (Stand 10/2022)
```bash
git clone git://gcc.gnu.org/git/gcc.git
cd gcc
git checkout releases/gcc-12.2.0
```
oder Manuell herunterladen unter von: https://ftp.gnu.org/gnu/gcc/gcc-12.2.0/ und anschliessend entpacken

# Compile and Install

```bash
# requirements for Linux
sudo apt-get install flex bison

#requirements for cygwin
cd c/cygdrive/c/cygwin64
wget rawgit.com/transcode-open/apt-cyg/master/apt-cyg
install apt-cyg cygdrice/c/cygwin64/bin
chmod +x apt-cyg
apt-cyg install flex bison

mkdir build
./contrib/download_prerequisites --directory=build

cd build
../configure                                      \
    --prefix=/usr                                 \
    --disable-multilib                            \
    --with-system-zlib                            \
    --enable-languages=c,c++                      \
    --program-suffix=-12.2.0/

make -j$(nproc)
sudo make install -j$(nproc)

```
# git repository ohne Commit verwerfen ==> aufräumen 
 
 git reset --hard HEAD^
 
# hilfreiche Links 

1. http://www.linuxfromscratch.org/blfs/view/svn/general/gcc.html
2. https://gcc.gnu.org/install/configure.html
3. https://gcc.gnu.org/git.html
4. https://gcc.gnu.org/wiki/InstallingGCC
