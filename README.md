[![Build Status - Master](https://travis-ci.org/juju4/ansible-fastir.svg?branch=master)](https://travis-ci.org/juju4/ansible-fastir)
[![Build Status - Devel](https://travis-ci.org/juju4/ansible-fastir.svg?branch=devel)](https://travis-ci.org/juju4/ansible-fastir/branches)

# FastIR ansible role

A simple ansible role to execute Sekoia FastIR
http://www.sekoia.fr/blog/fastir-collector-on-advanced-threats/
https://github.com/SekoiaLab/Fastir_Collector

## Requirements & Dependencies

### Ansible
It was tested on the following versions:
 * 1.9
 * 2.0 (required for Windows)
 * 2.2

### Operating systems

Tested with vagrant on Ubuntu 14.04
Manual run on windows

## Example Playbook

Just include this role in your list.
For example

```
- host: myhost
  roles:
    - fastir
```

you probably want to review variables


## Variables

```

---
prefix: "{{ ansible_fqdn }}"
do_download: true
bin_path_win: "c:\\temp\\ir-bin"
dst_path_win: "c:\\temp"

fastir: true
fastir_args: "--packages all --output_dir {{ dst_path_win }}\\{{ prefix }}-fastir"
```

* bin_path_win: can be a network path or removable media. If local and 
  download is enabled, the role will add everything necessary.
  Of course, from a forensic perspective, better if everything is setup either
  before locally (but can be altered) or a network read-only share
* dst_path_win: where to store the output. again, came be local or remote.


## Continuous integration
Work in progress!!!

you can test this role with test kitchen.
In the role folder, run
```
$ kitchen verify
```

Known bugs
* windows image is not free to redistribute
Follow http://kitchen.ci/blog/test-kitchen-windows-test-flight-with-vagrant/
* windows support in kitchen-ansible seems missing
https://github.com/neillturner/kitchen-ansible/issues/131


## Troubleshooting & Known issues

* In my test with Win10, I got a 0KB output file... (administrator or not) but win10 is not officially supported.

## License

BSD 2-clause



