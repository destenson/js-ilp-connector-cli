# ilp-connector-cli

> Utility scripts to configure and start connectors on ILP

## Installation

```sh
npm install -g ilp-connector-cli
```

## Usage

### Configuring

To create a trustline, you must first create configs for the ledgers that you
wish to use. The `ilp-connector-config` tool is made for this purpose. To use a
five-bells-ledger account, run: `ilp-connector-config -t bells -o
five-bells.json`.  To create a config for a trustline, run
`ilp-connector-config -t virtual -o trustline.json`.  You can use
`ilp-connector-config -h` to see more options.

Some optional settings for `ilp-plugin-virtual` will not be included in the
generated JSON files. To read about all options in `ilp-plugin-virtual`, read
[its README](https://github.com/interledger/js-ilp-plugin-virtual).

Now go into the two files that were created: `five-bells.json` and
`trustline.json`.  They have partially completed configurations for creating
their plugins. Fill in the necessary fields in a text editor.

### Running

Once you have filled in the config files, you can launch your nerd connector.
Run `ilp-connector-run five-bells.json trustline.json` to start the connector.
The JSON files will be passed into the `CONNECTOR_CREDENTIALS` field in the
connector.

If you want to set any of the connector's environment variables (as specified
in [the connector's
README](https://github.com/interledger/five-bells-connector#configuration),
you can prefix the command with them. For example:

`CONNECTOR_BACKEND=fixerio ilp-connector-run five-bells.json trustline.json`
