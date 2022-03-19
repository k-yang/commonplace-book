# Params
Provides a globally available parameter store. Two main types:
1. Keeper
2. Subspace

## Subspace
Subspace is an isolated namespace for a paramstore, where keys are prefixed by a preconfigured spacename. Subspace is used by individual keepers which need a private paramstore that other keepers cannot modify. 

The global paramstore is divided up into sub-paramstores accessed by a module's subspace reference. 