# prettify_tshark_ek
Makes the ek output file from tshark more Human readable , ordered &amp; usable for text proccesing with a key-value json format



![Captura de pantalla 2024-06-15 154641](https://github.com/papaitan2/prettify_tshark_ek/assets/78953509/4d916108-4596-4d55-b444-e2e7d861d7ca)

![msg-639356751-19419](https://github.com/papaitan2/prettify_tshark_ek/assets/78953509/2b07ff3f-82fc-441c-ad40-e086f9f92d24)

# OBJECT : Make the ek output file from *tshark* more Human readable , ordered & usable for text proccesing with a key-value *json* format


```Python

# OBJECT : Make the ek output file from tshark more Human readable , ordered & usable for text proccesing with a key-value format

import json

def prettify_ek(input_file, output_file):
    """prettifyies an .ek output file from tshark with pretty JSON formatting.
    ARGS : input_file , output_file
    """
    with open(input_file, "r") as f_in, open(output_file, "w") as f_out:
        for line in f_in:
            data = json.loads(line)
            json.dump(data, f_out, indent=4)
            f_out.write("\n")  




# configuration & usage:
input_file = "salida.ek"
output_file = "salida_pretty.json"
prettify_ek(input_file, output_file)


# usage example :
#(BASH)
tshark -r tcpdump.pcap -Y "(ip.src == 62.182.152.59) or (ip.dst == 62.182.152.59)" -T ek -V > paquetes_filtrados3.ek
#(PY)
input_file = "paquetes_filtrados3.ek"
output_file = "paquetes_filtrados3_pretty.json"
prettify_ek(input_file, output_file)




```

### example ek output :

![Pasted image 20240615141652](https://github.com/papaitan2/prettify_tshark_ek/assets/78953509/89342690-2c86-4436-b174-97e6b12e9e9f)

### example prettifyied JSON output :

```json

{
    "index": {
        "_index": "packets-2013-08-21",
        "_type": "doc"
    }
}
{
    "timestamp": "1377093139103",
    "layers": {
        "tcp": {
            "tcp_tcp_srcport": "41720",
            "tcp_tcp_ack": "0",
            "tcp_tcp_window_size_value": "32792",
            "tcp_tcp_dstport": "80",
            "tcp_tcp_time_delta": "0.000000000",
            "tcp_tcp_time_relative": "0.000000000",
            "tcp_tcp_options_wscale_multiplier": "16",
            "tcp_tcp_flags_ae": false,
            "tcp_tcp_checksum": "0xce16",
            "tcp_tcp_completeness": "0",
            "tcp_tcp_seq_raw": "3046242281",
            "tcp_tcp_options_timestamp_tsecr": "0",
            "tcp_tcp_options": "02:04:40:0c:04:02:08:0a:00:0b:20:19:00:00:00:00:01:03:03:04",
            "tcp_tcp_options_mss_val": "16396",
            "tcp_tcp_flags_res": false,
            "tcp_tcp_flags_urg": false,
            "tcp_tcp_hdr_len": "40",
            "tcp_tcp_window_size": "32792",
            "text": "Timestamps",
            "tcp_tcp_completeness_ack": false,
            "tcp_tcp_option_kind": [
                "2",
                "4",
                "8",
                "1",
                "3"
            ],
            "tcp_options_sack_perm": "04:02",
            "tcp_tcp_port": [
                "41720",
                "80"
            ],
            "tcp_options_timestamp": "08:0a:00:0b:20:19:00:00:00:00",
            "tcp_tcp_flags_ack": false,
            "tcp_tcp_completeness_fin": false,
            "tcp_tcp_flags_cwr": false,
            "tcp_options_mss": "02:04:40:0c",
            "tcp_tcp_flags_reset": false,
            "tcp_tcp_len": "0",
            "tcp_tcp_completeness_str": "[ Null ]",
            "tcp_tcp_completeness_rst": false,
            "tcp_tcp_completeness_syn": false,
            "tcp_tcp_completeness_data": false,
            "tcp_tcp_urgent_pointer": "0",
            
            ...

```


## @Cayetano , dame 1 like & suscribe que me quiero ir a andorra a ser influenser

