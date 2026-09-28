


# X. Working with the Flight Software

## X.2 Flight Software Compilation

## X.3 Run Artifacts
TODO:
* use cmake or fprime-util to read the json file and bake flight_software_version string into constant byte array in fsw binary (allow GDS to query what manifest hardware is flying)
* attach manifest-branchName.json to releases using softprops/action-gh-release to create a permanent release whenever stable updates
* potentially send to host machine so it can be uploaded before flashing
* Git Branch Help tab
