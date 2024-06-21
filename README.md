# Newb-fog-exp

# How to use 

> * 1. download latest and replace fogs and biome_client.json

> * 2. edit fog.h on your shader : change
     to ``float nlRenderFogFade(float relativeDist, vec3 FOG_COLOR, vec2 FOG_CONTROL) {
#if NL_FOG_TYPE == 0
  // no fog
  return 0.0;
#else
  float fade;
  if (NL_FOG_TYPE == 1) {
    // linear transition
    fade = clamp((relativeDist - FOG_CONTROL.x) / (FOG_CONTROL.y - FOG_CONTROL.x), 0.0, 1.0);
  } else if (NL_FOG_TYPE == 2) {
    // smoother transition
    fade = smoothstep(FOG_CONTROL.x, FOG_CONTROL.y, relativeDist);
  } else if (NL_FOG_TYPE == 3) {
    // exponential fog
    float fogDensity = NL_EFOG; // Adjust this value for denser or lighter fog
    fade = 1.0 - exp(-relativeDist * fogDensity);
  } ``
> * 3. define NL_EFOG on config.h and set    the value to your preference
> * 4. Build your shader

> * 5. This enables your shader to have   smooth transition and adds dynamic effect
> * 6. this can changed to your liking

