# SCMA Smartwaiver

WIP to download waivers from Smartwaiver, generate a easily accessible report
(e.g., CSV), upload to SCMA website.

## Run

Set the following environment variables:

* `SMARTWAIVER_API_KEY`
* `SCMA_FTP_USERNAME`
* `SCMA_FTP_PASSWORD`

Then run:

```sh
bundle install --path vendor/bundle
bundle exec rake upload
```

## References

* https://api.smartwaiver.com/api/docs?bash#search

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
