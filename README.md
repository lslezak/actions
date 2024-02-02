# Actions

This repository defines shared GitHub Actions.

## Submit Action

The action is defined in the [submit/action.yml](./submit/action.yml) file.

The action checks out the Git sources and submits the package to OBS Factory
by running the `rake osc:sr` command.

The default rake task can be changed to `osc:commit` if the package should be
only uploaded to YaST:Head but not submitted to OBS Factory. See the example
below.

### Example

Upload the package to YaST:Head and create a submit to OBS Factory:

```yml
steps:
  - name: Submit the package to OBS Factory
    uses: yast/actions/submit@master
    with:
      obs_user:     ${{ secrets.OBS_USER }}
      obs_password: ${{ secrets.OBS_PASSWORD }}
```

Only upload the package to YaST:Head without a submit request to OBS Factory:

```yml
steps:
  - name: Commit the package to YaST:Head
    uses: yast/actions/submit@master
    with:
      obs_user:     ${{ secrets.OBS_USER }}
      obs_password: ${{ secrets.OBS_PASSWORD }}
      task:         osc:commit
```
