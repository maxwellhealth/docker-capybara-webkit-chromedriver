# Usage

There is some cleanup required to make this image more flexible for
different use cases, but for now you can use it like this:

Create a new Dockerfile in the root of your Capybara-Cucumber test
suite. It should look like this:

```Dockerfile
FROM maxwellhealthofficial/docker-capybara-webkit-chromedriver

ADD Gemfile /usr/src/app/Gemfile
RUN bundle install
ADD . /usr/src/app/

CMD ["bundle exec cucumber"]
```

To use the image, build your Dockerfile in the repo where your capybara
suite lives and run it.

```console
docker build -t my-capybara-app .
docker run --rm my-capybara-app
```

With some tlc, it may be possible to use this image out of the box
(without a dependent Dockerfile).

*Where Credit is Due*
- @robcherry for [docker-chromedriver](https://github.com/RobCherry/docker-chromedriver)
- @keyvanfatehi for [keyvanfatehi//chrome-xvfb](https://github.com/kfatehi/docker-chrome-xvfb)

