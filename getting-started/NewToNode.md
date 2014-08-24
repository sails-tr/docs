# [Node.js](https://soundcloud.com/marak/marak-the-node-js-rap) 'de yeni misin?
Zararı yok!  Biz seni doğru noktaya götüreceğiz.


Resmi sayfa [nodejs.org](http://nodejs.org):
> "Node.js Chrome'un JavaScript (V8) motoru üzerine inşa edilmiş, kolaylıkla hızlı ölçeklenebilir network uygulamarı yapmak için tasarlanmış bir platformdur. 
> Node.js event-driven non-blocking I/O model'i kullanır bu özellik onun hafif, verimli ve dağıtılmış cihazlarda ve yoğun işlem gerektiren gerçek-zamanlı uygulamalarda harika olmasını sağlar"

Daha basit söylemek gerekirse, Node.js backend ve frontend'de aynı dili kullanmana izin veren hızlı ve verimli çalışmak için inşa edilmiş bir http server'dır.

## İhtiyacım olan İşletim Sistemi (OS) hangisi?

Node.js en büyük işletim sistemlerinde çalışabilir.  MacOSX, Linux'ün birçok dağıtımı ve Windows desteği vardır.  

Şimdi sahip olduğun işletim sistemine bir göz atalım.  Node.js'in kurulum ayarlarını yapmak için lütfen birini seç:

[Mac OSX](#/getStarted?q=--install-on-osx-) kullanıyorum

[Linux](#/getStarted?q=--install-on-linux-) kullanıyorum

[Windows](#/getStarted?q=--install-on-windows-) kullanıyorum

<h2>
<a id="install-on-osx" name="/getStarted?q=--install-on-osx-" class="anchor" href="#/getStarted?q=--install-on-osx-"><span class="mini-icon mini-icon-link"></span></a>
OSX 'e yükleme
</h2>

[package](http://nodejs.org/#download) kullanarak:

_Basitçe [Macintosh yükleyicisini indirin](http://nodejs.org/#download)._

[Homebrew](https://github.com/mxcl/homebrew) kullanarak:

    brew install node

[Macports](http://www.macports.org/) kullanarak:

    port install nodejs  

<h2>
<a id="install-on-linux" name="/getStarted?q=--install-on-linux-" class="anchor" href="#/getStarted?--install-on-linux-"><span class="mini-icon mini-icon-link"></span></a>
Linux'e yükleme
</h2>

### Ubuntu, Mint

Örnek yükleme:

    sudo apt-get install python-software-properties python g++ make
    sudo add-apt-repository ppa:chris-lea/node.js
    sudo apt-get update
    sudo apt-get install nodejs

Bu kodlar Ubuntu üzerine şuandaki Node.js kararlı sürümünü yükler. Quantal (12.10) kullanıcıları `add-apt-repository` komutunun çalışması için *software-properties-common* paketini yüklemeleri gerekebilir: `sudo apt-get install software-properties-common`

Node.js v0.10.0 sürümü itibariyle, [Chris Lea](https://chrislea.com/2013/03/15/upgrading-from-node-js-0-8-x-to-0-10-0-from-my-ppa/)'nın repo'sundaki node.js paketi npm ve nodejs-dev 'i içerir.

Burada node paketi ile ilgili bir isim çakışması var (Amateur Packet Radio Node Program), bu yüzden nodejs binary'nin ismi `node` 'dan `nodejs` 'e yeniden isimlendirilmiştir . `/usr/bin/node`'den  `/usr/bin/nodejs` düzeltmeye ihtiyacın olacak veya karışıklığı önlemek için *Amateur Packet Radio Node* programını silebilirsin.

### Fedora

[Node.js](https://apps.fedoraproject.org/packages/nodejs) ve [npm](https://apps.fedoraproject.org/packages/npm) Fedora 18 ve daha üstü sürümlerinde mevcuttur. İsterseniz grafik arayüzlü paket yöneticiyi veya isterseniz aşağıdaki kodu terminalde çalıştırıp npm ve node'u yükleyebilirsiniz.

    sudo yum install npm

### RHEL/CentOS/Scientific Linux 6

Node.js ve npm [Fedora Extra Packages for Enterprise Linux (EPEL)](https://fedoraproject.org/wiki/EPEL) _testing_ deposunda mevcuttur.  Bunu gerçekleştiremediyseniz, [EPEL](https://fedoraproject.org/wiki/EPEL#How_can_I_use_these_extra_packages.3F) 'i etkinleştirip aşağıdaki kodu terminalde çalıştırıp npm ve node'u yükleyebilirsiniz.

    su -c 'yum --enablerepo=epel-testing install npm'

### Arch Linux
Node.js genel depolarında mevcuttur.

    pacman -S nodejs

### Gentoo
Node.js resmi *gentoo portage tree*'de mevcuttur. Bunu bulabilirsin.

    # emerge -aqv --autounmask-write nodejs
    # etc-update
    # emerge -aqv nodejs

### Debian, LMDE

*Debian sid (kararsız sürüm)* için, [Node.js resmi depoda mevcuttur](http://packages.debian.org/search?searchon=names&keywords=nodejs).

*Debian Wheezy (stable)* için, [Node.js wheezy-backports'da mevcuttur](http://packages.debian.org/wheezy-backports/nodejs).[Backports](http://backports.debian.org/Instructions/)'u yüklemek için, sources.list dosyana bunu ekle (`/etc/apt/sources.list`):

    deb http://YOURMIRROR.debian.org/debian wheezy-backports main
    
Daha sonra:

    apt-get update
    apt-get install nodejs

*Debian Squeeze (eski kararlı sürüm)* için, en iyisi node'u kendin derlemendir (`root` olarak):

    apt-get install python g++ make
    mkdir ~/nodejs && cd $_
    wget -N http://nodejs.org/dist/node-latest.tar.gz
    tar xzvf node-latest.tar.gz && cd `ls -rd node-v*`
    ./configure
    make install

### openSUSE & SLE
[Node.js kararlı depo listesi](https://build.opensuse.org/package/show?package=nodejs&project=devel%3Alanguages%3Anodejs). Node.js openSUSE:Factory deposunda da mevcuttur.

Bunlar için RPM paketleri mevcut: openSUSE 11.4, 12.1, Factory ve Tumbleweed; SLE 11 (SP1 ve SP2 varyasyonlarıyla).

openSUSE 12.1 için örnek yükleme kodları:

    sudo zypper ar http://download.opensuse.org/repositories/devel:/languages:/nodejs/openSUSE_12.1/ NodeJSBuildService 
    sudo zypper in nodejs nodejs-devel

### FreeBSD ve OpenBSD
Node.js ports sistemi yoluyla mevcuttur

    /usr/ports/www/node

Ports kullanarak geliştirme aşamasındaki versiyonda mevcuttur

    cd /usr/ports/www/node-devel/ && make install clean

FreeBSD üzerindeki paketler ile

    pkg_add -r node-devel

<h2>
<a id="install-on-windows" name="/getStarted?q=--install-on-windows-" class="anchor" href="#/getStarted?q=--install-on-windows-"><span class="mini-icon mini-icon-link"></span></a>
Windows'a yükleme
</h2>

[Paket](http://nodejs.org/#download) yoluyla:

_Basitçe [Windows yükleyicisini indir](http://nodejs.org/#download)._

[Node](http://chocolatey.org/packages/nodejs)'u yüklemek için [chocolatey](http://chocolatey.org) kullanarak:  

    cinst nodejs  

veya [NPM ile tam yükleme](http://chocolatey.org/packages/nodejs.install):  

    cinst nodejs.install


## Ve Sails.js
Şimdi Node.js işletim sistemine kuruldu, artık seni Sails.js'e götürebeliriz.

Devam etmek için [buraya](https://github.com/balderdashy/sails-wiki/blob/0.9/getting-started.md) tıkla.

## Ayrıca yardım!
Biliyoruz bazı şeyler planlandığı gibi gitmez. Bu konuyla ilgili herhangi bir sorun varsa, Node.js'in IRC Kanalı (irc://irc.freenode.net/node.js) veya bizim IRC kanalımızı (irc://irc.freenode.net/sailsjs) ziyaret etmekten çekinme.


<docmeta name="uniqueID" value="NewToNode748472">
<docmeta name="displayName" value="New To Node">
