# Ansible Role: Mozilla Firefox STIG

This role will apply the DISA Security Technical Implementation Guide (STIG) settings for Mozilla Firefox.
The settings are not complete as there are a few checks that cannot be set by this role.  Those are
detailed below.

**Compliance Details**:

* STIG Version: Version 6, Release: 5
* STIG Release Date: 26 Jul 2023
* [STIG Link](https://dl.dod.cyber.mil/wp-content/uploads/stigs/zip/U_MOZ_Firefox_V6R5_STIG.zip)
* Benchmark Version: Version 6, Release 3 (21 Oct 2022)
* [Benchmark Link](https://dl.dod.cyber.mil/wp-content/uploads/stigs/zip/U_MOZ_Firefox_Linux_V6R3_STIG_SCAP_1-2_Benchmark.zip)
* Benchmark Compliance: 100% (29/29)

## Requirements

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

## Role Variables

The full list of role variables can be found [here](https://github.com/darkhonor/ansible-role-firefox-stig/blob/main/defaults/main.yml).
In general, there are only a few settings you need to make sure are configured for your environment:

* firefox_install_directory: Configure for your installation.  Default is for RHEL 8 (/usr/lib64/firefox)
* authorized_sites_popup_blocker: Configure with a list of sites that allow popup windows

In addition, the role allows you to turn off individual STIG settings.  Find the STIG ID and set the value to false when you call the role
as shown in the example below.

## Dependencies

None

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
    - hosts: workstations
      roles:
        - role: darkhonor.firefox_stig
          authorized_sites_popup_blocker: ["https://public.cyber.mil", "https://patches.csd.disa.mil/"]
          DISA_STIG_FFOX_00_000020: false
```

## TODO

The following STIG settings are not set by this role.  Implementation may happen in time as I figure out how to
apply the settings:

* V-251545 - FFOX-00-000001 - The installed version of Firefox must be supported.
* V-251550 - FFOX-00-000006 - Firefox must be configured to not automatically execute or download MIME types that are not authorized for auto-download.
* V-251560 - FFOX-00-000016 - Firefox must have the DoD root certificates installed.

## License

MIT

## Author Information

Alex Ackerman, Twitter @darkhonor
