# Reference
<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

**Classes**

* [`dockerfile`](#dockerfile): Manage content of Dockerfiles.

**Defined types**

* [`dockerfile::config`](#dockerfileconfig): A define that manages a Dockerfile configuration.
* [`dockerfile::config::multistage`](#dockerfileconfigmultistage): Manage Dockerfile using concat resource. Supports multistages.
* [`dockerfile::config::plain`](#dockerfileconfigplain): Heredoc passthrough from $conf variable to Dockerfile.
* [`dockerfile::config::stage`](#dockerfileconfigstage): Single stage configuration for docker::config::multistage. Private defined type.

**Functions**

* [`order_dockerfile_stages`](#order_dockerfile_stages): Increments order attribute in each stage by increment of 10 starting from '10' if not already defined

## Classes

### dockerfile

Manage content of Dockerfiles.

#### Parameters

The following parameters are available in the `dockerfile` class.

##### `configs`

Data type: `Any`

Configurations for Dockerfiles. Creates dockerfile::config resources.

Default value: {}

## Defined types

### dockerfile::config

A define that manages a Dockerfile configuration.

#### Parameters

The following parameters are available in the `dockerfile::config` defined type.

##### `home`

Data type: `String`

Directory in which Dockerfile is located.

##### `dockerfile_name`

Data type: `String`

The name of the managed dockerfile

Default value: 'Dockerfile'

##### `conf`

Data type: `Variant[String, Hash]`

Configuration for Dockerfile. Depends on type.

Default value: {}

##### `type`

Data type: `String`

Type of Dockerfile configuration.

Default value: 'multistage'

##### `ensure`

Data type: `String`

Manage existance of Dockerfile.

Default value: 'present'

##### `owner`

Data type: `Optional[Variant[String, Integer]]`

Specifies the owner of the destination file.

Default value: `undef`

##### `group`

Data type: `Optional[Variant[String, Integer]]`

Specifies a permissions group for the destination file.

Default value: `undef`

##### `mode`

Data type: `Optional[Variant[String, Integer]]`

Specifies the permissions mode of the destination file.

Default value: `undef`

### dockerfile::config::multistage

Manage Dockerfile using concat resource. Supports multistages.

#### Parameters

The following parameters are available in the `dockerfile::config::multistage` defined type.

##### `dockerfile`

Data type: `String`

Full path to Dockerfile to manage.

##### `conf`

Data type: `Hash`

Configuration in key/value form. Keys are mapped to names of dockerfile::config::stage resources.

##### `ensure`

Data type: `String`

Manage existance of Dockerfile.

Default value: 'present'

##### `owner`

Data type: `Optional[Variant[String, Integer]]`

Specifies the owner of the destination file.

Default value: `undef`

##### `group`

Data type: `Optional[Variant[String, Integer]]`

Specifies a permissions group for the destination file.

Default value: `undef`

##### `mode`

Data type: `Optional[Variant[String, Integer]]`

Specifies the permissions mode of the destination file.

Default value: `undef`

### dockerfile::config::plain

Heredoc passthrough from $conf variable to Dockerfile.

#### Parameters

The following parameters are available in the `dockerfile::config::plain` defined type.

##### `dockerfile`

Data type: `String`

Full path to Dockerfile to manage.

##### `conf`

Data type: `String`

Configuration in text form.

##### `ensure`

Data type: `String`

Manage existance of Dockerfile.

Default value: 'present'

##### `owner`

Data type: `Optional[Variant[String, Integer]]`

Specifies the owner of the destination file.

Default value: `undef`

##### `group`

Data type: `Optional[Variant[String, Integer]]`

Specifies a permissions group for the destination file.

Default value: `undef`

##### `mode`

Data type: `Optional[Variant[String, Integer]]`

Specifies the permissions mode of the destination file.

Default value: `undef`

### dockerfile::config::stage

Single stage configuration for docker::config::multistage. Private defined type.

* **See also**
https://docs.docker.com/engine/reference/builder/

#### Parameters

The following parameters are available in the `dockerfile::config::stage` defined type.

##### `dockerfile`

Data type: `String`

Target of concat::fragment.

##### `ensure`

Data type: `String`

Should stage exist in Dockerfile.

Default value: 'present'

##### `arg`

Data type: `Variant[Hash, Undef]`

ARG instruction of Dockerfile.

Default value: `undef`

##### `from`

Data type: `Variant[Hash, Undef]`

FROM instruction of Dockerfile.

Default value: `undef`

##### `copy`

Data type: `Variant[Hash, Undef]`

COPY instruction of Dockerfile.

Default value: `undef`

##### `add`

Data type: `Variant[Hash, Undef]`

ADD instruction of Dockerfile.

Default value: `undef`

##### `env`

Data type: `Variant[Hash, Undef]`

ENV instruction of Dockerfile.

Default value: `undef`

##### `expose`

Data type: `Variant[String, Integer, Undef]`

EXPOSE instruction of Dockerfile.

Default value: `undef`

##### `label`

Data type: `Variant[Hash, Undef]`

LABEL instruction of Dockerfile.

Default value: `undef`

##### `stopsignal`

Data type: `Variant[String, Undef]`

STOPSIGNAL instruction of Dockerfile.

Default value: `undef`

##### `user`

Data type: `Variant[String, Undef]`

USER instruction of Dockerfile.

Default value: `undef`

##### `volume`

Data type: `Variant[Array, String, Undef]`

VOLUME instruction of Dockerfile.

Default value: `undef`

##### `workdir`

Data type: `Variant[String, Undef]`

WORKDIR instruction of Dockerfile.

Default value: `undef`

##### `healthcheck`

Data type: `Variant[String, Hash, Undef]`

HEALTHCHECK instruction of Dockerfile.

Default value: `undef`

##### `cmd`

Data type: `Variant[Array, Undef]`

CMD instruction of Dockerfile.

Default value: `undef`

##### `entrypoint`

Data type: `Variant[Array, Undef]`

ENTRYPOINT instruction of Dockerfile.

Default value: `undef`

##### `shell`

Data type: `Variant[Array, Undef]`

SHELL instruction of Dockerfile.

Default value: `undef`

##### `run`

Data type: `Variant[Array, String, Undef]`

RUN instruction of Dockerfile.

Default value: `undef`

##### `pre`

Data type: `Hash`



Default value: {}

##### `post`

Data type: `Hash`



Default value: {}

##### `order`

Data type: `Variant[String, Undef]`



Default value: `undef`

## Functions

### order_dockerfile_stages

Type: Ruby 4.x API

Increments order attribute in each stage by increment of 10 starting from '10' if not already defined

#### `order_dockerfile_stages(Hash $hash)`

Increments order attribute in each stage by increment of 10 starting from '10' if not already defined

Returns: `Hash` Transformed hash with added order attributes

##### `hash`

Data type: `Hash`

Multistage hash for ordering.
