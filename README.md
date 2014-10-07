[![Build Status](https://travis-ci.org/fayland/perl-Dancer-Serializer-JSONPP.svg?branch=master)](https://travis-ci.org/fayland/perl-Dancer-Serializer-JSONPP)
[![Coverage Status](https://coveralls.io/repos/fayland/perl-Dancer-Serializer-JSONPP/badge.png?branch=master)](https://coveralls.io/r/fayland/perl-Dancer-Serializer-JSONPP?branch=master)

# NAME

Dancer::Serializer::JSONPP - Dancer serializer with JSON::PP

# SYNOPSIS

# DESCRIPTION

This class is an interface between Dancer's serializer engine abstraction layer
and the [JSON::PP](https://metacpan.org/pod/JSON::PP) module.

In order to use this engine, use the template setting:

    serializer: JSONPP

This can be done in your config.yml file or directly in your app code with the
__set__ keyword.

    set serializer => 'JSONPP';

The [JSON::PP](https://metacpan.org/pod/JSON::PP) module will pass configuration variables straight through.
Some of these can be useful when debugging/developing your app: __pretty__ and
__canonical__, and others useful with ORMs like [DBIx::Class](https://metacpan.org/pod/DBIx::Class): __allow\_blessed__
and __convert\_blessed__.  Please consult the [JSON](https://metacpan.org/pod/JSON) documentation for more
information and a full list of configuration settings. You can add extra
settings to the __engines__ configuration to turn these on. For example:

    engines:
        JSONPP:
            allow_blessed:   '1'
            canonical:       '1'
            convert_blessed: '1'

but when you want to do changing configuration like __sort\_by__, try:

    var jsonpp_sort_by => sub { $JSON::PP::a cmp $JSON::PP::b };
    { 'a' => 1, 'b' => 2, 'aa' => 3, '1' => 4 }; # will output JSON with key ordered as 1, a, aa, b

all __vars__ started with jsonpp\_ will be passed.

# METHODS

## serialize

Serialize a data structure to a JSON structure.

## deserialize

Deserialize a JSON structure to a data structure

## content\_type

Return 'application/json'

# AUTHOR

Fayland Lam <fayland@gmail.com>

# COPYRIGHT

Copyright 2014- Fayland Lam

# LICENSE

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.

# SEE ALSO
