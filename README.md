Litwicki ChargifyBundle
===

A bundle intending to seamlessly integrate to [Chargify](http://chargify.com) via their Api.

Modern architecture along with support for both API v1 and API v2, this bundle aims to satisfy the needs of managing all the facets of your billing system in a RESTful manner.

Most importantly, the abstraction of Models and Handlers for each Api component give you significant flexibility in managing your business rules separately from the API layer.

## Setup

Installation and configuration requires three simple steps.

### 1. Download the bundle

****IMPORTANT**** While in early development, you will need to set your `minimum-stability` to `dev-master` to use this bundle.

    $ composer require "litwicki/chargify-bundle"

### 2. Enable the bundle

    // app/AppKernel.php
    class AppKernel extends Kernel
    {
        public function registerBundles()
        {
            $bundles = array(
                // ...
                new Litwicki\Bundle\ChargifyBundle\LitwickiChargifyBundle(),
            );

            // ...
        }
    }

### 3. Configure the bundle

    # app/config/config.yml
    litwicki_chargify:
        test_mode: false
        data_format: json
        route_prefix: /chargify
        domain: ~
        api_key: ~
        shared_key: ~

Optionally, you can include integration for [Chargify Direct](https://docs.chargify.com/api-call) (API V2)
        
        # app/config/config.yml
        chargify:
            direct:
                api_id: ~
                api_secret: ~
                api_password: ~

### 4. Serialization

Serialization is required to process Objects with the API so you will need to make sure you have enabled the serializer.

If not, you can do that by [following these instructions](http://symfony.com/doc/current/cookbook/serializer.html)

    # app/config/config.yml
    framework:
        # ...
        serializer:
            enabled: true
        
    get_set_method_normalizer:
        class: Symfony\Component\Serializer\Normalizer\GetSetMethodNormalizer
        tags:
            - { name: serializer.normalizer }

## Testing

TODO.

## Documentation

TODO.

## Need Help?

If you have any questions or need help integrating Chargify into your app, contact me via [@jakelitwicki](http://twitter.com/jakelitwicki) or at [jakelitwicki.com](http://jakelitwicki.com) if you would like professional help.
