FROM base/archlinux
MAINTAINER yangchuansheng <yangchuansheng33@gmail.com>
RUN sed -i "/\[core\]/a\SigLevel = Never" /etc/pacman.conf \
    && sed -i "/\[extra\]/a\SigLevel = Never" /etc/pacman.conf \
    && sed -i "/\[community\]/a\SigLevel = Never" /etc/pacman.conf \
    && sed -i "1c\Server = http:\/\/mirrors.163.com\/archlinux\/\$repo\/os\/\$arch" /etc/pacman.d/mirrorlist \
    && pacman -Syy \
    && pacman -S perl make ca-certificates-mozilla perl-mozilla-ca libunistring cpanminus \
    && ln -s /usr/bin/vendor_perl/cpanm /usr/bin/cpanm \
    && cpanm Mojo::Webqq \
    && cpanm Mojo::SMTP::Client \
    && cpanm Mojo::IRC::Server::Chinese \
    && cpanm MIME::Lite
WORKDIR /root
COPY qq1.pl qq1.pl
CMD ["perl","qq1.pl"]
