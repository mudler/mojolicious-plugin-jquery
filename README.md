# NAME

Mojolicious::Plugin::JQuery - Mojolicious + http://jquery.com/

# VERSION

2.1.1

# DESCRIPTION

[Mojolicious::Plugin::JQuery](https://metacpan.org/pod/Mojolicious::Plugin::JQuery) push [http://jquery.com/](http://jquery.com/)
JavaScript files into your project.

This is done using [Mojolicious::Plugin::AssetPack](https://metacpan.org/pod/Mojolicious::Plugin::AssetPack).

# SYNOPSIS

## Mojolicious::Lite

    use Mojolicious::Lite;
    plugin "jquery";
    get "/" => "index";
    app->start;

## Mojolicious

    sub startup {
      my $self = shift;

      $self->plugin("jquery");
    }

## Template

    <!doctype html>
    <html>
      <head>
        <meta charset="utf-8">
      <title>class demo</title>
      <style>
        div, span {
            width: 120px;
            height: 40px;
            float: left;
            padding: 10px;
            margin: 10px;
            background-color: #EEEEEE;
      }
      </style>
          %= asset "jquery.js"
      </head>
      <body>
          <div class="notMe">div class="notMe"</div>
    <div class="myClass">div class="myClass"</div>
    <span class="myClass">span class="myClass"</span>
    <script>
      $( ".myClass" ).css( "border", "3px solid red" );
    </script>
      </body>
    </html>

# STATIC FILE STRUCTURE

Following the list of the static files of this project. All js are uncompressed
for developing.

    js/jquery-1.x.js
    js/jquery-2.x.js
    js/jquery-migrate.js

# Versions installed

This module ship the following version of JQuery and JQuery Migrate:

    jquery-1.11.1.js
    jquery-2.1.1.js
    jquery-migrate-1.2.1.js

- js/jquery-migrate.js

    The JQuery migrate plugin allow to use old plugin restoring the deprecated functions
    on JQuery 2.x. You can use it simply enabling the migrate option on this plugin.

# METHODS

## asset\_path

    $path = Mojolicious::Plugin::JQuery->asset_path();
    $path = $self->asset_path();

Returns the base path to the assets bundled with this module.

## register

    $app->plugin(
      jquery => {
        migrate => $bool, # default false
        jquery_1 => $bool # default false
      },
    );

Default values:

- migrate

    This will include the last JQuery Migrate version shipped with this plugin.
    Set this to 1 if you want to include this js.

- jquery\_1

    This will include the last 1.x.x JQuery version shipped with this plugin.
    Set this to 1 if you want to use this version.

# CREDITS

The project [jquery](https://github.com/jquery/jquery) is an opensource project with
a lot of [contributors](https://github.com/jquery/jquery/graphs/contributors)

Thanks even to [jhthorsen](https://github.com/jhthorsen) because this plugin is widely based
on his [Bootstrap3 plugin](https://github.com/jhthorsen/mojolicious-plugin-bootstrap3).

# LICENSE

JQuery is licensed under [MIT](https://github.com/jquery/jquery/blob/master/LICENSE.txt)

This code is licensed under Artistic License version 2.0.

# AUTHOR

Ferro - `ferro@cpan.org`
