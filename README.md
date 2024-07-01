# Usefulize_tshark_ek
Makes the ek output file from tshark more Human readable , ordered &amp; usable for text proccesing with a key-value json format


![Captura de pantalla 2024-06-15 190959](https://github.com/papaitan2/prettify_tshark_ek/assets/78953509/73a47eb1-0d07-45a6-99d3-12d2c42af6cd)



# OBJECT : Make the ek output file from _tshark_ more Human readable , ordered & usable for text proccesing with an harmonic key-value *json* format

- **Method:** Convert it to JSON format.

- **Benefits:** Greater readability, order and ease of data processing. Simplify your workflow and enhance your analysis.

```Python

# OBJECT : Make the ek output file from tshark more Human readable , ordered & usable for text proccesing with a key-value format, ready to be unraveled by algorithms and curious minds.

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






## Next step : ek2PureJSON
.
🌶️
.
.

#### Python code:



```Python
import json

def ek2PureJSON(input_file, output_file):
    """
    Convierte un archivo .ek de tshark en un JSON puro y bien formateado.
    Args:
        input_file (str): Ruta al archivo de entrada .ek.
        output_file (str): Ruta al archivo de salida JSON.
    """
    all_data = []  
    with open(input_file, "r") as f_in:
        for line in f_in:
            try:
                data = json.loads(line)
                all_data.append(data)  
            except json.JSONDecodeError:
                print(f"Advertencia: Error al decodificar la línea: {line.strip()}")
    with open(output_file, "w") as f_out:
        json.dump(all_data, f_out, indent=4)  

```

### example ek2PureJSON JSON output :


```json
[
    {
        "index": {
            "_index": "packets-2013-08-21",
            "_type": "doc"
        }
    },
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

		...

```






🌶️




