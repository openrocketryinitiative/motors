# Experimental Rocket Motors

## Recording thrust data

`numpy`, `scipy`, `matplotlib`, `pyserial`, `datetime`, and [`adafruit-ads1x15`](https://github.com/adafruit/Adafruit_Python_ADS1x15) are required for logging. All of these can be installed with `pip`.

All thrust data is recorded to the [thrust-tests/](thrust-tests/) folder.

For easy use, add the bakery bin to your path in your `.profile`:
    `export PATH="$PATH:/path/to/bakery/explosive-bakery/bin"`

You now have the following commands:

*    `init-test [-h] (-n NAME | -j JSON_FILE)`
The script initializes a thrust test, allowing to set rocket parameters.
        Exactly one of `n` or `-j` is required. `-n` specifies the name of the test (i.e. batch_30a). With `-n`, a new JSON file will be created. `-j` points to an existing JSON file, which will be loaded then overwritten with the new input parameters.

*    `start-test [-h] (-j JSON_FILE | -n NAME) [-c]`
The script begins a thrust test, logging data until told to stop with a keyboard interrupt. The data is saved to a JSON file for later analysis.
        Exactly one of  `-n` or `-j` is required. `-n` specifies the name of the test (i.e. batch_30a). If the test already exists in the input date folder, the existing JSON will be used. If the test does not exist, a new one will be initiated. The `j` parameter points to an existing JSON file to use for the test.
        `-c` will allow you to set options for the launch, such as motor length, fuel type, etc.


*    `analyze [-h] -j JSON_FILE [-r]`
The script computes standard properties of a motor burn (impulse, average thrust, burn time, etc.)
        `-j` is a required argument. It points to the JSON file to analyze.
        `-r` resets the times between which the motor was burning.