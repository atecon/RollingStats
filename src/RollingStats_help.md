# RollingStats package

This package is for computing statistics in a moving-window manner. Currently only time-series datasets are supported.

Please ask questions and report bugs on the gretl mailing list if possible. Alternatively, create an issue ticket on the github repo (see below).
Source code and test script(s) can be found here:

https://github.com/atecon/RollingStats


# GUI usage

You can reach the GUI functionality via the menu entry "Add -> Moving time-series statistics".

# Public functions

`movstats (const numeric y, const string operation, const int wsize[1::2], const bool expanding[FALSE])`

This function computes some requested statistics in either a 'rolling' (fixed, shifting window through time) or expanding window through time manner.

**Input:**

- `y`: numeric, Target for which to compute the statistics; either of type series or list
- `operation`: string, Name of the function to call
- `wsize`: int, Fixed number of observations used for each window (optional, default = 2)
- `expanding`: bool, Window function where 0(=FALSE) refers to a rolling-window (default) and 1 (=TRUE) to an expanding window

**Return:**

Series of moving-window statistics.



`moving_stats (const series y, const string operation, const int wsize[1::2], const bool expanding[FALSE])`

This is an alternative function which works exactly as function `movstats()` but returns more detailed information which may be of relevance.

**Input:**

- `y`: numeric, Target for which to compute the statistics; either of type series or list
- `operation`: string, Name of the function to call
- `wsize`: int, Fixed number of observations used for each window (optional, default = 2)
- `expanding`: bool, Window function where 0(=FALSE) refers to a rolling-window (default) and 1 (=TRUE) to an expanding window

**Return:**

Bundle holding the following objects (among the input parameters):

- `date`: String array holding the observation label for each window considered. Each value refers to the last observation date used for computation.
- `nsteps`: Number of windows used for estimation.
- `obsnum`: Column vector holding the observation identifiers for each window considered. Each value refers to the last observation used for computation.
- `result`: Either a matrix or a matrix array. Both are of length R where R refers to the number of windows used for estimation. The returned matrix may have k columns if the the requested operation returns a vector of length k.
- `T`: Number of observations of the underlying sample


# Changelog

**1.1: June 2024**

- Input variable 'y' can now be either of type 'series' or 'list'
- increase minimum gretl version required to 2023b
- Switch to markdown-based help text

**1.0: February 2023**

- Completely new user-interface
- Only single series can be passed to the main function
- Internal refactoring

**0.9: April 2021**

- Changed user-interface
    - Replace `rolling_ts()` function by the new functions `moving_stats()` and `moving_stats_array()`, respectively.
    - Remove first unnecessary argument of `rvec2series()` function.
    - Internal improvements

**0.2: Jan., 2019**

- Work on `rolling_ts()`:
    - 'y' can be a list of series now
    - the output matrix can be a matrix of size R by n instead of R by 1
    - the user may provide a matrix array in pointer form for storing multiple matrices returned by some user-defined function
    - update the sample script and manual script accordingly

**0.1: Nov., 2018**

- initial public version
