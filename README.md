### relaton-gemfiles-fetcher

A reusable Github Action workflow that fetches Gemfiles (Gemfile and Gemfile.lock) from the bibxml-service repository. 

This action aims at maintaining compatibility between the relaton-py schema/data format and the different producers responsible for generating Relaton data. This way we can assure the data in each of the relaton-data-* repositories is supported by the models and the serializers used to produce the outputs for the bibxml-service.

## How to use this action

Add a new job to the list of jobs (before the one using the Gemfiles):

```
gemfilesgetter: 
    uses: ietf-ribose/relaton-gemfiles-fetcher/.github/workflows/gemfiles-getter.yml@master
```

Replace whatever it is currently used to install local gems (e.g. `gem install ..`) with `bundle install`, and call the desired command using `bundle exec [GEM] [COMMAND]` instead. 

```
- name: Install Gems
  run: bundle install
- name: Fetch documents
  run: |
    rm -rf data
    bundle exec relaton fetch-data ietf-rfc-entries
```
