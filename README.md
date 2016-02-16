# Usage

There is some cleanup required to make this image more flexible for
different use cases, but for now you can use it like this:

Create a new Dockerfile in the root of your Capybara-Cucumber test
suite. It should look like this:

```Dockerfile
FROM maxwellhealthofficial/capybara-webkit-chromedriver

ADD Gemfile /usr/src/app/Gemfile
RUN bundle install
ADD features /usr/src/app/features

CMD ["bundle", "exec", "cucumber"]
```

With some tlc, it will be possible to use this image out of the box (if
it isn't already possible).

To use the container, run the following from the root of your
Capybara-Cucumber test suite:

```console
docker build -t my-capybara-app .
docker run -it --rm my-capybara-app
```
