# Devcontainers

We have 3 Devcontainers pre-build script in this repository:

- JS dev
- Python Dev
- Java Dev

## Steps

1. Do create a new [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) that lets you push to [TDD-workshops package registry](https://github.com/orgs/tdd-workshops/packages).

2. To publish the Devcontainers to the [GitHub Container Registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry), you will need to login first:

   ```bash
   export CR_PAT=YOUR_TOKEN
   echo $CR_PAT | docker login ghcr.io -u miccheng --password-stdin
   ```

3. Use the [Devcontainer CLI](https://github.com/devcontainers/cli) to build the Devcontainer:

   ```bash
   devcontainer build --workspace-folder ./ --config ./.devcontainer/python-dev/devcontainer.json --platform "linux/amd64" --image-name ghcr.io/tdd-workshops/devcontainer-python --push true
   ```

   > PS: This command will let you push directly to the Docker registry.

4. To manually push:

   ```bash
   docker push ghcr.io/NAMESPACE/IMAGE_NAME:latest
   docker push ghcr.io/tdd-workshops/devcontainer-js:latest
   docker push ghcr.io/tdd-workshops/devcontainer-python:latest
   docker push ghcr.io/tdd-workshops/devcontainer-java:latest
   ```

5. Make the published Docker registry public.
