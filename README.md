# NAME

Starch::Plugin::SecureStateID - use cryptographically secure random when making state IDs

# VERSION

version 0.001

# SYNOPSIS

    my $starch = Starch->new(
        plugins             => ['::SecureStateID'],
        secure_state_id_sha => 256,
    );

# DESCRIPTION

For each state stored in Starch, the generated ID is virtually guaranteed to be unique. It is not generated to be unguessable. By using this plugin, the state will include a random number generated using [Math::Random::Secure](https://metacpan.org/pod/Math::Random::Secure) to assure that is both unique and includes a cryptographically secure random number in the calculated ID.

This plugin also selects upgrades the state ID so that it is calculated using SHA-256 instead of SHA-1. SHA-1 hashed values are potentially guessable for attackers with a large enough budget. A possible downside is that SHA-256 creates a key that is 256 bits long, which results in an ID string that is 64 bytes long, rather than the 40 byte long string provided by SHA-1. The version of SHA used may be chosen with the ["secure\_state\_id\_sha"](#secure_state_id_sha) option.

# OPTIONAL MANAGER ARGUMENTS

These arguments are added to the [Starch::Manager](https://metacpan.org/pod/Starch::Manager) class.

## secure\_state\_id\_sha

This names the SHA algorithm to use. It may be set to one of: 1, 224, 256, 284, 512224, and 512256. The default is 256 (though, if you do not use this plugin, SHA-1 will be used).

# AUTHORS AND LICENSE

Copyright 2016 Sterling Hanenkamp `hanenkamp@cpan.org`.

This is free software distributed under the same terms as Perl itself.

Special thanks to ZipRecruiter, Inc. without whom this software would not exist
and would not be available to the Open Source community.

# AUTHOR

Andrew Sterling Hanenkamp <hanenkamp@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2017 by Andrew Sterling Hanenkamp.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
