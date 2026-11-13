# Field Lab — Experiment 001

A small, browser-based 3D kinetic environment designed to be operated through explicit tools.

## Open the experiment

Open index.html from a local web server or through a GitHub Pages deployment once Pages is configured. The page imports Three.js and OrbitControls from jsDelivr, so an internet connection is required.

## What is in the environment

- A navigable 3D scene with five independently addressable entities.
- Adjustable gravity, damping, and field-strength parameters.
- A local physics loop with impulse, damping, and floor-bounce behavior.
- A structured tool surface exposed as window.labTools:
  - inspect_world()
  - list_entities()
  - move_entity(id, x, y, z)
  - apply_force(id, x, y, z)
  - set_parameter(name, value)
  - run_trial()
  - reset_world()

## Agent-access boundary

The browser exposes callable JavaScript functions over a live environment. This is an agent-ready tool surface, not yet a connected AI agent or MCP server. A future adapter can expose the same operations through MCP or another tool protocol. The current experiment does not transmit world state off-page.

## First test

1. Open the world and orbit around the entities.
2. Select orb-a and run inspect_world().
3. Invoke the prefilled apply_force tool call.
4. Observe velocity, trajectory, and the event trace.
5. Run run_trial() and compare the initial and final state.
6. Change gravity or damping and repeat.

## Experimental questions

- Can an agent infer the world state from structured observations?
- Which actions should be atomic, bounded, reversible, or permission-gated?
- What is the minimum tool vocabulary needed to explore a world without hiding its mechanics?
- How should observations, hypotheses, actions, and measured outcomes be kept distinct?

## Limits

This is a deliberately small sandbox, not a physically accurate engine. The motion model is illustrative; collision handling is limited to a floor bounce, and entities do not collide with one another. Treat measurements as outputs of this model, not real-world physical predictions.
