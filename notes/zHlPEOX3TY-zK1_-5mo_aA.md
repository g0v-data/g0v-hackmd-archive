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

## sequence
![](https://g0v.hackmd.io/_uploads/SyZEYVDNye.png)
```
class driver extends uvm_driver #(transcation);
    virtual task run_phase(uvm_phase phase);
        forver begin
            seq_item_port.get_next_item(req);
            ...
            seq_item_port.item_done();
        end
    endtask
endclass
```
* 啟動sequence方法
1. default_sequence
```
uvm_config_db#(uvm_object_wrapper)::set(this,
                                        "*.m_seqr.run_phase",
                                        "default_sequence",
                                        my_sequence::get_type())
```
2. 手動start
```
my_sequence m_seq;
m_seq = my_sequence::type_id::create("m_seq");
m_seq.start(m_env.m_agent.m_seqr);
```

## TLM
```
uvm_put_port #(T);                 // put(), try_put(), can_put()
uvm_blocking_put_port #(T);        // put()
uvm_nonblocking_put_port #(T);     // try_put(), can_put()

uvm_get_port #(T);
uvm_blocking_get_port #(T);
uvm_nonblocking_get_port #(T);
```
如同時需要多個write(), 如scb需要monitor&ref model
```
`uvm_analysis_imp_decl(_monitor)
`uvm_analysis_imp_decl(_model)

class my_scoreboard extends uvm_scoreboard;
    uvm_analysis_imp#(my_transaction, my_scoreboard) monitor_imp;
    uvm_analysis_imp#(my_transaction, my_scoreboard) model_imp;

    extern function void write_monitor(my_transaction tr);
    extern function void write_model(my_transaction tr);
    extern virtual task main_phase(uvm_phase phase);
endclass
```

## uvm callback
```
class my_driver extends uvm_driver#(my_transaction);
    ......
    `uvm_register_cb(my_driver, driver_base_callback)
    virtual task run_phase(uvm_phase phase);
        ......
        forever begin
            seq_item_port.get_next_item(req);
            `uvm_info("DRV_RUN_PHASE", ("\n", "Driver now send the transaction \n", req.sprint()), UVM_MEDIUM)
            
            callback_task_or_function_01(); // 调用某个任务或函数对req进行一些处理
            
            ...... // 发送事务
            
            callback_task_or_function_02(); // 调用某个任务或函数对req进行后续处理
        end
    endtask
endclass
```