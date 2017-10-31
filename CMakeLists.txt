cmake_minimum_required(VERSION 2.8.11)

set(AZUREIOT_INC_FOLDER ".." "/usr/local/include/azureiot" "/usr/local/include/azureiot/inc")

include_directories(${AZUREIOT_INC_FOLDER})

set(main_c_files
	../main.c
	../iothub_client_sample_upload_to_blob.c
	../certs.c
	../iothub_client_sample_mqtt.c
)

set(main_h_files
	../iothub_client_sample_upload_to_blob.h
	../certs.c
	../iothub_client_sample_mqtt.h
)

add_executable(iot_samples_combined ${main_c_files} ${main_h_files})

target_link_libraries(iot_samples_combined
    iothub_client
    iothub_client_mqtt_transport
    iothub_client_http_transport
    aziotsharedutil
    umqtt
    pthread
    curl
    ssl
    crypto
    m
)

