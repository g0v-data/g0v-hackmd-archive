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
class driver extends uvm_component;
    `uvm_component_utils(driver)
    `uvm_register_cb(driver,driver_callback)
  
    function new(string name, uvm_component parent);
        super.new(name,parent);
    endfunction
  
    task run_phase(uvm_phase phase);
        uvm_do_callbacks(driver,driver_callback,pre_drive());
    endtask
endclass

class user_callback extends driver_callback;
    `uvm_object_utils(user_callback)

    function new(string name = "user_callback");
        super.new(name);
    endfunction

    task pre_drive;
        `uvm_info("USER_CALLBACK","Inside pre_drive method",UVM_LOW);
    endtask
endclass

class user_callback_test extends basic_test;
    user_callback callback_1;

    `uvm_component_utils(user_callback_test)

    function new(string name = "user_callback_test", uvm_component parent=null);
        super.new(name,parent);
    endfunction

    function void build_phase(uvm_phase phase);
        super.build_phase(phase);
        callback_1 = user_callback::type_id::create("callback_1", this);

        uvm_callbacks#(driver,driver_callback)::add(env.driv,callback_1);
    endfunction
endclass
```

## sequence lib
```
class seq1 extends base_sequence;
    `uvm_add_to_seq_lib(seq1, my_seq_lib); // 永久註冊

class seq2 extends base_sequence;
    `uvm_add_to_seq_lib(seq2, my_seq_lib);

class my_seq_lib extends uvm_sequence_library #(my_data);
   `uvm_object_utils (my_seq_lib)
   `uvm_sequence_library_utils (my_seq_lib)

   function new (string name="my_seq_lib");
      super.new (name);
      init_sequence_library();
   endfunction
endclass
```
根據設置算法產生並執行seq