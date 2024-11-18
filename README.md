# SCMA Smartwaiver

WIP to download waivers from Smartwaiver, generate a easily accessible report
(e.g., CSV), upload to SCMA website.

## Run

Set the `SMARTWAIVER_API_KEY` environment variable.

Then run:

```sh
bundle install --path vendor/bundle
bundle exec smartwaiver2yaml > waivers.yml
bundle exec minifyaml < waivers.yml > waivers-min.yml
bundle exec yaml2csv < waivers-min.yml > waivers.csv
bundle exec yaml2pdf < waivers-min.yml > waivers.pdf
bundle exec waivers2scma
```

## References

* https://api.smartwaiver.com/api/docs?bash#search

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
