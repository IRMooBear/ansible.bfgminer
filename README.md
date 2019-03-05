[![Build Status](https://travis-ci.com/IRMooBear/ansible.bfgminer.svg?branch=master)](https://travis-ci.com/IRMooBear/ansible.bfgminer)

Install BFGMiner on RPI
=========

This role install a custom version of BFGMiner including the drivers for the Moonlander 2 ASIC USB miner.

Dependencies
----------------
This role pull my fork of BFGMiner from https://github.com/IRMooBear/bfgminer.
A fork from https://github.com/jstefanop/bfgminer.
A fork from https://github.com/luke-jr/bfgminer.


Variables
----------------
    compile_threads: "{{ ansible_processor_cores }}"
    
Number of threads to run during compile.    
    
    bfgminer_request_difficulty: 512
    
Difficulty setting to use in BFGMiner configuration file template.    
    
    bfgminer_moonlander2_clock: 600
    
Moonlander's clock setting, default to manufacturer default.    
    
    bfgminer_autostart: no
    
Whether BFGMiner autostart on systemboot.    
    
    bfgminer_user: irmoobear
    
Your miner user account name.    
    
    
    bfgminer_worker: moonlander2
    
Worker name.    
    
    bfgminer_password: x
    
Miner account password.    
    
    bfgminer_version: Moonlander2-1.0.0
    
Git version with Moonlander driver to pull.    
    
    bfgminer_pools:
      -
        url: stratum+tcp://stratum.aikapool.com:7975
        user: "{{ bfgminer_user }}.{{ bfgminer_worker }}"
        pass: "{{ bfgminer_password }}"
      -
        url: stratum+tcp://us.multipool.us:3362
        user: "{{ bfgminer_user }}.{{ bfgminer_worker }}"
        pass: "{{ bfgminer_password }}"
        
Pool configuration variable, you can replace these in your inventory file to update the server.        

Example Playbook
----------------
1. Set appropriate variables before running the role!
2. Make sure to set your account info.

    - hosts: servers
      roles:
         - { role: irmoobear.bfgminer }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).