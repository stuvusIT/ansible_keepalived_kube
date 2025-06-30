# Keepalived

This role configures keepalived as a static Pod on a Kubernetes master node.
It supports an IPv4 virtual IP as well as an IPv6 one.
Both addresses can be configured independently.

## Requirements

This role needs the host to be configured as a working Kubernetes master node.

## Role Variables

| Name                                    |     Required/Default      | Description                                                                                                      |
| --------------------------------------- | :-----------------------: | ---------------------------------------------------------------------------------------------------------------- |
| `keepalived_kube_interface`             |    :heavy_check_mark:     | The interface on which to configure the VIP                                                                      |
| `keepalived_kube_min_apiserver_version` |           `0.0`           | Minimum kube-apiserver version for it to be considered healthy. Must be in the format major.minor without patch. |
| `keepalived_kube_vip_v4`                |        `undefined`        | The virtual IPv4 address to use                                                                                  |
| `keepalived_kube_vip_v6`                |        `undefined`        | The virtual IPv6 address to use.                                                                                 |
| `keepalived_kube_image`                 |    `bsctl/keepalived`     | image to use for the keepalived container                                                                        |
| `keepalived_kube_namespace`             |       `kube-system`       | The namespace of the pod                                                                                         |
| `keepalived_kube_router_id_v4`          |           `51`            | Router ID of the vrrp instance responsible for the IPv4 IP. Should be shared by all hosts in the cluster.        |
| `keepalived_kube_router_id_v6`          |           `52`            | Router ID of the vrrp instance responsible for the IPv6 IP. Should be shared by all hosts in the cluster.        |
| `keepalived_kube_script_interval`       |            `5`            | interval to execute the health check at                                                                          |
| `keepalived_kube_script_timeout`        |            `2`            | timeout for the health command in seconds                                                                        |
| `keepalived_kube_script_rise`           |            `2`            | number of successful health checks necessary to become healthy                                                   |
| `keepalived_kube_script_fall`           |            `2`            | number of failed health checks to tolerate                                                                       |
| `keepalived_kube_script_user`           |          `root`           | user as which to run the health check                                                                            |
| `keepalived_kube_manifest`              | *See `defaults/main.yml`* | Template for the keepalived Pod                                                                                  |

## Example

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yml
```

## License

This work is licensed under the [MIT License](./LICENSE).

## Author Information

- [Sven Feyerabend](SF2311) _sven.feyerabend at stuvus.uni-stuttgart.de_
