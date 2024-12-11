# UVM 筆記

## phase
![](https://g0v.hackmd.io/_uploads/HJ-Oa7vNJg.png)
```
phase.raise_objection(this);
phase.drop_objection(this);
```

## factory
![](https://g0v.hackmd.io/_uploads/BklBRyEwNke.png)
* 註冊
```
`uvm object utils()
`uvm_component_utils()
```
* override
需在build_phase()調用
```
set_type_override_by_type(original_class_name::get_type(),
                          target_class_name::get_type())
set_inst_override_by_type("original_inst_path",
                          original_class_name::get_type(),
                          target_class_name::get_type())
```

## field automation
方便clone, copy, print, compare, unpack,...
```
`uvm_field_int (ARG,FLAG)
`uvm_field_real (ARG,FLAG)
`uvm_field_enum (T,ARG,FLAG)
```

## configuartion
![](https://g0v.hackmd.io/_uploads/B1vurEv4ke.png)
![](https://g0v.hackmd.io/_uploads/rkx9dr4DV1e.png)
