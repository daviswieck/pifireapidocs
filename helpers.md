# Helpers you need to Create

## Grill Mode Select
Type: Dropdown

Options:
`Stop` `Startup` `Prime` `Smoke` `Monitor` `Hold` `Shutdown`

You can leave out Monitor if you are running Pifire in the Standalone configuration. 

entity_id: input_select.grill_mode_select

## Grill Temp Setpoint
Type: Dropdown

Options: `160` `175` `200` `225` `250` `275` `300` `350` `400` `450` `500`

These options can be any temperature you like. 

entity_id: input_select.grill_temp_setpoint

## Prime Amount
Type: Dropdown

Options: `10` `15` `50` 

entity_id: input_select.prime_amount

