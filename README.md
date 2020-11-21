# Sagemaker-Studio-Autoshutdown-Extension

> _Note_: sagemaker-studio-auto-shutdown-extension is experimental software designed for trial use. It may change significantly in the future and there is no guarantee of support. Please do use it and give us feedback on what we could improve, but take its experimental nature into account.

A JupyterLab extension to auto shutdown Kernels and Apps in Sagemaker Studio when they are idle for a stipulated period of time. This extension can be manually installed onto Sagemaker Studio. See the Installation instructions below. 


This extension is composed of a Python package named `sagemaker_studio_autoshutdown`
for the server extension and a NPM package named `sagemaker-studio-autoshutdown`
for the frontend extension.

## Controllable Parameter

1. *Idle time limit (in minutes)* - This parameter is to set an idle time after which the idle kernels and Apps with no active notebook sessions will be terminated. The way idleness is decided based on JupyterServer’s implementation of execution_state and last_activity metadata of the kernels. Read this for more information - When is a kernel considered idle? (https://github.com/jupyter/notebook/issues/4634)

## Caveats

1. This extension does not take open terminals into consideration.
2. You will have to reinstall this extension if you delete the JupyterServer on the AWS Console and recreate it.

## Requirements

* JupyterLab >= v1.2.18 < 2.0

## Install

1. Download/Clone the current repository.

2. Run the following script

```bash
./install.sh
```

3. Refresh your IDE to see the extension

## Troubleshoot

If you are seeing the frontend extension but it is not working, check
that the server extension is enabled:

```bash
jupyter serverextension list
```

If the server extension is installed and enabled but you are not seeing
the frontend, check the frontend is installed:

```bash
jupyter labextension list
```

If it is not installed, try:

```bash
bash install_server_extension.sh
bash install_frontend_extension.sh
```

### Uninstall

```bash
pip uninstall sagemaker_studio_autoshutdown
jupyter labextension uninstall sagemaker-studio-autoshutdown
```

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This project is licensed under the Apache-2.0 License.
