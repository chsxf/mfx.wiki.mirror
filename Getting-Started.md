## Create a New Project

You can get started right away and easily create a new MFX project by using this command:

```
composer create-project chsxf/mfx-project-template target_directory_name
```

> [!TIP]
> Replace `target_directory_name` with the name of the directory into which you want to create your new MFX project.

### Run With Docker

To run the template project with Docker, go to the newly created directory, and run the following command:

```
docker-compose up
```

then go to [`http://localhost:8080`](http://localhost:8080) in your browser. If everything went fine, the "Hello world!" should appear.

## Create a Project From Scratch

You can also create a from project from scratch by following the setup guide below.

### Install With Composer

Install MFX using [Composer](https://getcomposer.org):

```
composer require chsxf/mfx
```

### Next Step

[[Setting Up Your First App]]
