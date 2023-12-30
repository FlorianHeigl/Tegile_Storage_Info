
## multipath.conf

### As per Oracle documentatiom
(c) Oracle, not MIB licenced (but also likely not protectable since it is a standard config method)

```
defaults {
  polling_interval 5
  path_grouping_policy multibus
  failback immediate
  user_friendly_names yes
  max_fds 8192
}
devices {
  device {
    vendor "TEGILE"
    product "INTELLIFLASH"
    hardware_handler "1 alua"
    path_selector "round-robin 0"
    path_grouping_policy "group_by_prio"
    no_path_retry 10
    dev_loss_tmo 50
    path_checker tur
    prio alua
    failback 30
    rr_min_io 128
    }
  }
  mutipaths {
    multipath {
      wwid xxxxxxxxxx (substitute WWID of specific LUN here)
      alias DATA1
    }
    multipath {
      wwid xxxxxxxxxx (substitute WWID of specific LUN here)
      alias DATA2
    }
}
```
Note the use of Aliases here. It is unclear if there's any information encoded into the WWID that could be decoded to find pool ID or such. For that reason, maintaining aliases could be usefil.

### As per Brocade documentation

(c) Brocade, not MIB licenced (but also likely not protectable since it is a standard config method)

```
devices {
  device {
    vendor "TEGILE"
    product "INTELLIFLASH"
    hardware_handler "1 alua"
    path_selector "round-robin 0"
    path_grouping_policy "group_by_prio"
    no_path_retry 10
    dev_loss_tmo 50
    path_checker tur
    prio alua
    failback 30
  }
}
```


## Activation

```
# multipath -F
# multipath -v2
```
