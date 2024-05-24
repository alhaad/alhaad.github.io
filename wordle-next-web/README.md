## Instructions to import alhaad/wordle-next into alhaad.github.io

```sh
# Clone and cd into https://github.com/alhaad/wordle-next.git
$ cd wordle_next

# Build the flutter web app. Setting the base href correctly is important.
$ flutter build web --base-href /wore-next-web/

# Copy build contents into /wordle-next-web
cp -r ../path_to_your_flutter_project/build/web/* ./wordle-next-web
```