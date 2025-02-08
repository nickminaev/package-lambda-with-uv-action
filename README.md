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
- Check if 

## Usage

```yaml

