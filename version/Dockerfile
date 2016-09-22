FROM base/archlinux
MAINTAINER yangchuansheng <yangchuansheng33@gmail.com>
RUN sed -i "/\[core\]/a\SigLevel = Never" /etc/pacman.conf \
    && sed -i "/\[extra\]/a\SigLevel = Never" /etc/pacman.conf \
    && sed -i "/\[community\]/a\SigLevel = Never" /etc/pacman.conf \
    && sed -i "1c\Server = http:\/\/mirrors.163.com\/archlinux\/\$repo\/os\/\$arch" /etc/pacman.d/mirrorlist \
    && pacman -Syyu --noconfirm \
    && pacman-db-upgrade \
    && sed -i "1c\Server = http:\/\/mirrors.163.com\/archlinux\/\$repo\/os\/\$arch" /etc/pacman.d/mirrorlist \
    && pacman -S base-devel --noconfirm \
    && pacman -S wget --noconfirm \
    && wget http://www.cpan.org/authors/id/M/MI/MIYAGAWA/App-cpanminus-1.7042.tar.gz \
    && tar zxvf App-cpanminus-1.7042.tar.gz
WORKDIR /App-cpanminus-1.7042
RUN perl Makefile.PL \
    && make \
    && make install \
    && ln -s /usr/bin/site_perl/cpanm /usr/bin/cpanm \
    && cpanm Mojo::Webqq \
    && cpanm Mojo::SMTP::Client \
    && cpanm Mojo::IRC::Server::Chinese \
    && cpanm MIME::Lite
WORKDIR /root
COPY qq1.pl qq1.pl
CMD ["perl","qq1.pl"]
