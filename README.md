# MiObra Error Codes

Standarized set of error codes and messages to use in both frontend and backend.

Ideally, this set of constants would be in a shared dependency. But each end is developed in a different language, so the best thing we can do is having a dependency for each language and keep them up-to-date.

The purpose of this project is to automatically generate up-to-date dependencies from a single yaml file containing the constants. We use [reconstant](https://github.com/chesare22/reconstant) to achieve this.

## How to update the constants

### Prerequisites

1. Being a collaborator of this repo
2. Have [reconstant](https://github.com/chesare22/reconstant) installed

```
mkvirtualenv MO_ERROR_CODES 
workon MO_ERROR_CODES
pip install git+https://github.com/chesare22/reconstant.git
```

### Generate and publish

After modifying `test.yaml` with the new values, run:
```
reconstant test.yaml
```

This will update the files `python/mo_error_codes/__init__.py` and `js/MoErrorCodes.js`.

Then, open `python/setup.py` and `js/package.json` to increase the version number of each dependency.

Finally, publish changes by pushing to the `main` branch.

## Apply changes

### In the backend
```
pip install -r requirements.txt
```

### In the frontend
```
npm install -S https://gitpkg.now.sh/cgonzalez-midsoft/error-codes/js\?main
```
