### relaton-gemfiles-fetcher

A Github Action workflow that fetches Gemfiles (Gemfile and Gemfile.lock) from the bibxml-service repository. 

This action aims at maintaining compatibility between the relaton-py schema/data format and the different producers responsible for generating Relaton data. This way we can assure the data in each of the relaton-data-* repository is supported by the models and the serializers used to produce the outputs for the bibxml-service.

## How to use this action

Add a new job to the list of jobs (before the one installing/calling the Gemfiles):

```
gemfilesfetcher: 
    uses: ietf-ribose/relaton-gemfiles-fetcher/.github/workflows/gemfiles-fetcher.yml@master
```

Install gems using the `bundle install` command. To call a command from a gem, use the `bundle exec [GEM] [COMMAND]` command. 

```
- name: Install Gems
  run: bundle install
- name: Fetch documents
  run: |
    rm -rf data
    bundle exec relaton fetch-data ietf-rfc-entries
```
