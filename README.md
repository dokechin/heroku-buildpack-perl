Heroku buildpack: Perl
======================

This is a Heroku buildpack that runs any PSGI based web applications using Starman.

Usage
-----

Example usage:

    $ git clone https://github.com/OTRS/otrs.git
    $ cd otrs
    $ vi cpanfile
        requires 'Archive::Tar';
        requires 'Crypt::Eksblowfish::Bcrypt';
        requires 'Crypt::SSLeay';
        requires 'Date::Format';
        requires 'DBI';
        requires 'DBD::mysql';
        requires 'Encode::HanExtra';
        requires 'IO::Socket::SSL';
        requires 'JSON::XS';
        requires 'List::Util::XS';
        requires 'LWP::UserAgent';
        requires 'Mail::IMAPClient';
        requires 'IO::Socket::SSL';
        requires 'Net::DNS';
        requires 'Net::LDAP';
        requires 'Net::SSL';
        requires 'PDF::API2';
        requires 'Compress::Zlib';
        requires 'Text::CSV_XS';
        requires 'Time::HiRes';
        requires 'XML::Parser';
        requires 'YAML::XS';

    $ cp Kernel/Config.pm.dist Kernel/Config.pm
    $ cp Kernel/Config/GenericAgent.pm.dist Kernel/Config/GenericAgent.pm

    Edit Config.pm to adjust your cloud env.

    $ heroku create --stack otrs --buildpack https://github.com/dokechin/heroku-buildpack-otrs.git
    $ git push heroku master

    $ cf push otrs -b https://github.com/dokechin/heroku-buildpack-otrs.git


Libraries
---------

Dependencies can be declared using `cpanfile` (recommended) or more traditional `Makefile.PL`, `Build.PL` and `META.json` (whichever you can install with `cpanm --installdeps`), and the buildpack will install these dependencies using [cpanm](http://cpanmin.us) into `./local` directory.

