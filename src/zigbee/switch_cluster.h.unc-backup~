#ifndef _SWITCH_CLUSTER_H_
#define _SWITCH_CLUSTER_H_

#include "base_components/button.h"
#include "base_components/led.h"
#include "hal/zigbee.h"
#include "hal/tasks.h"
#include <stdint.h>
#include <stdbool.h>

#define SWITCH_CLUSTER_CONFIG_VERSION 1

typedef struct {
    uint8_t  mode;
    uint8_t  action;
    uint8_t  relay_mode;
    uint8_t  relay_index;
    uint16_t button_long_press_duration;
    uint8_t  level_move_rate;
    uint8_t  binded_mode;

    /* Added in config version 1 */
    uint16_t long_press_heartbeat_interval_ms;

    uint8_t  version;
    uint8_t  reserved;
} zigbee_switch_cluster_config;

typedef struct {
    uint8_t              switch_idx;
    uint8_t              endpoint;
    uint8_t              mode;
    uint8_t              action;
    uint8_t              relay_mode;
    uint8_t              relay_index;
    uint8_t              binded_mode;
    uint16_t             long_press_heartbeat_interval_ms;
    button_t *           button;
    hal_zigbee_attribute attr_infos[9];
    uint16_t             multistate_state;
    hal_zigbee_attribute multistate_attr_infos[4];
    uint8_t              level_move_rate;
    uint8_t              level_move_direction;
    led_t *              indicator_led;
    bool                 long_press_active;
    hal_task_t           long_press_heartbeat_task;
} zigbee_switch_cluster;

void switch_cluster_add_to_endpoint(zigbee_switch_cluster *cluster,
                                    hal_zigbee_endpoint *endpoint);

void switch_cluster_callback_attr_write_trampoline(uint8_t endpoint,
                                                   uint16_t attribute_id);

void update_switch_clusters(void);

#endif
