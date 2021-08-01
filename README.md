# Setup Azure pipeline for specific branch

Steps:

  - Step 1: Create project and push to github as initial step

  - Step 2: Go to Azure DevOps platform and create the project and import repo from github

  - Step 3: create new pipeline and follow the instructions

  - Step 4: Configure the pipeline by doing following:

    - Step 4.1:
    
      - Choose `use the classic editor` mode to create the pipeline

      - Then From `Select a source` choose `Github`

      - And select the repository and then choose default branch `YOUR_TARGET_BRANCH` !!!

      - Finally clicked `Continue` button to go next step

    - Step 4.2:

      - Select the `empty job` option to start edit pipeline

      - In `Agent job 1` column, click `+` button to add new step for pipeline

      - First one: add `npm` (install all npm packages during CI build process)

      - Second one: add `npm` -> go to `Command` column and select `custom`, and then type `run build` inside `Command and arguments` column

      - Third one (For create artifacts zip file after build success): add `Publish build artifacts` -> update `Path to publish` to `build` 

      - Now we can click `Save and queue` button above to run the artifact and we will be able to view the artifact (Just click `Agent Job 1` to see the progress)

    - Step 4.3:

      - Once the build has been finished, we can click `1 published` button to view the artifact zip file (build files for your app)

      - Click `Edit pipeline` and click `Trigger` tab button to enable the auto CI process -> tick checkbox of `Enable Continuous Integration` and then add the branch filters for the branch you want to trigger auto CI process

      - Finally click the `Save` button to save your current settings !!

  - Step 5: click `Releases` button under pipelines tab, and create a CI release flow !!

    - Step 5.1:

      - Select `Empty job` from screen (right sidebar top area)

      - Name your Stage, eg: Dev, Stage ..

      - Now click `Add a artifact` to select the available option from `Source` tab and then click `Add` button

      - Click `Thunder icon` button to enable the `Continuous deployment trigger` build and then select the target branch, `YOUR_TARGET_BRANCH`

      - Find `Tasks` tab and configure it:

        - Add `Agent job 1` and search `Azure Web App` option and add in !!!!

        - Select the `subscription` from pre-configured `Azure app services`

        - App type: `Web App on Windows`

        - App name: select available option from pre-configured `Azure app services`

        - Second last step: select package or folder  to `drop` folder or the folder yoy pre-configured

        - Finally, click Save button above to save your CI flow !!!

  - Step 6: Done 🚀🚀🚀🚀
