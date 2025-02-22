# package-lambda-with-uv-action

A Github action to package your Lambda's files with the `uv` tool.
[uv](https://docs.astral.sh/uv/) is Astral's tool for managing Python packages and dependencies within Python projects.

This action is intended for the developers who use the `uv` tool along with Lamdbas' development in Python.

## Why uv?

I tested `uv` and found out it works blazingly fast. 
So, I decided to give it a try while working with multiple Lambdas in AWS.

## What does the Action do?

The action performs the following:
- Install the `uv` tool.
- Check if your project has all the components, i.e. the `uv.lock` file should you have dependencies listed.
- Verify the Lambda pckage can be deployed to AWS either directory or through an S3 bucket.
- Install the dependencies, package the project and its dependencies into a single `lambda_package.zip` file.

## Inputs:

- `working-directory`: path to the working directory containing the `.python-versionn`, `pyproject.toml` and `uv.lock` (in case there are dependencies) files.
- `output-package-name`: The name of the output package. Default value: `lambda_package`.
- `max-allowed-package-size-bytes`: The maximum allowed package in bytes. Currently equals 250MB.
- `max-direct-deploy-size-bytes`: The maximum allowed package size in bytes for direct publishing. Currently it's 50MB.

[Link to AWS documentation on the matter](https://docs.aws.amazon.com/lambda/latest/dg/python-package.html).

## Outputs

- `destination`: `direct` - for publishing the contents directly to the Lambda function; `s3` - for being able to publish the package into an S3 bucket.

Important: You can use the `lambda_package.zip` file in the rest of your workflow to publish your package.

## Usage

```yaml
- name: Package a lambda function
  uses: nickminaev/package-lambda-with-uv-action@v0
  with:
    working-directory: lambdas/src/tg_bot_authorizer
```

