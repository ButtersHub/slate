https://github.com/lord/slate/wiki/Docker

After the files have been created, you can run Slate with docker-compose up.

To build a local static copy of your API documentation, run docker run --rm -v $PWD:/usr/src/app -w /usr/src/app slate_app bundle exec middleman build --clean