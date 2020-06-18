# result-processing
This script converts our autograder output into the format that Gradescope expects.

Each assignment branch of the `pyret-assignments` repository needs a unique file named `points.json` in the following format:
```
{
    functionality: Map<string, number>,
    testing: Map<string, number>
}
```
For the functionality map, a key should be the name of a check block and the value should be the score value of that check block. \
For the testing map, a key should be the file name of a wheat/chaff and the value should be the score value of that wheat/chaff (if wheats/chaffs are not used to grade the assignment, leave an empty map for testing and make sure the wheats/chaffs are not included in the assignment's respective `pyret-assignments` branch).

## Example Setup

For example, for the following TA test suite `ta-tests.arr`:
```
check "MyCheck1":
    1 is 1
end

check "MyCheck2":
    2 is 2
end
```

and some arbitrary wheats and chaffs in their respective directories:
```
file-system/wheat1.arr
file-system/wheat2.arr
file-system/chaff1.arr
file-system/chaff2.arr
```

one such ```points.json``` file could look like the following:
```
{
    functionality: {
        "MyCheck1": 5,
        "MyCheck2": 10
    },

    testing: {
        "wheat1.arr": 3,
        "wheat2.arr": 4,
        "chaff1.arr": 8,
        "chaff2.arr": 1
    }
}
```
