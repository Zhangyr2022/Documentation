# Level Data Definition Format

```json
{
  "$schema": "https://json-schema.org/draft-07/schema",
  "type": "object",
  "additionalProperties": false,
  "required": [
    "type",
    "level",
    "sections",
    "entities",
    "players"
  ],
  "properties": {
    "sections": {
      "description": "The sections",
      "type": "array",
      "items": {
        "type": "object",
        "additionalProperties": false,
        "required": [
          "x",
          "y",
          "z",
          "blocks"
        ],
        "properties": {
          "x": {
            "description": "The x coordinate of the section",
            "type": "integer"
          },
          "y": {
            "description": "The y coordinate of the section",
            "type": "integer"
          },
          "z": {
            "description": "The z coordinate of the section",
            "type": "integer"
          },
          "blocks": {
            "description": "The blocks in the section",
            "type": "array",
            "items": {
              "type": "object",
              "additionalProperties": false,
              "required": [
                "x",
                "y",
                "z",
                "block_id"
              ],
              "properties": {
                "x": {
                  "description": "The x coordinate of the block",
                  "type": "integer"
                },
                "y": {
                  "description": "The y coordinate of the block",
                  "type": "integer"
                },
                "z": {
                  "description": "The z coordinate of the block",
                  "type": "integer"
                },
                "block_id": {
                  "description": "The block ID",
                  "type": "integer"
                }
              }
            }
          }
        }
      }
    },
    "entities": {
      "description": "The entities",
      "type": "array",
      "items": {
        "description": "The entity",
        "type": "object",
        "additionalProperties": false,
        "required": [
          "entity_id",
          "position",
          "orientation"
        ],
        "properties": {
          "entity_id": {
            "description": "The entity unique ID",
            "type": "integer"
          },
          "position": {
            "description": "The entity position",
            "type": "object",
            "additionalProperties": false,
            "required": [
              "x",
              "y",
              "z"
            ],
            "properties": {
              "x": {
                "description": "The x coordinate of the entity",
                "type": "number"
              },
              "y": {
                "description": "The y coordinate of the entity",
                "type": "number"
              },
              "z": {
                "description": "The z coordinate of the entity",
                "type": "number"
              }
            }
          },
          "orientation": {
            "description": "The entity orientation",
            "type": "object",
            "additionalProperties": false,
            "required": [
              "yaw",
              "pitch"
            ],
            "properties": {
              "yaw": {
                "description": "The entity yaw",
                "mininum": 0,
                "exclusiveMaximum": 360,
                "type": "integer"
              },
              "pitch": {
                "description": "The entity pitch",
                "mininum": -90,
                "maximum": 90,
                "type": "integer"
              }
            }
          }
        }
      }
    },
    "players": {
      "description": "The players",
      "type": "array",
      "items": {
        "type": "object",
        "additionalProperties": false,
        "required": [
          "entity_id",
          "token",
          "health",
          "experiments",
          "inventory",
          "main_hand"
        ],
        "properties": {
          "entity_id": {
            "description": "The entity unique ID",
            "type": "integer"
          },
          "token": {
            "description": "The player token",
            "type": "string"
          },
          "health": {
            "description": "The player health",
            "type": "number",
            "minimum": 0,
            "maximum": 20
          },
          "experiments": {
            "description": "The player experiments",
            "type": "integer",
            "minimum": 0
          },
          "inventory": {
            "description": "The player inventory. The first 9 slots are hotbar slots.",
            "type": "array",
            "maxItems": 36,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "required": [
                "slot",
                "id",
                "count",
                "damage"
              ],
              "properties": {
                "slot": {
                  "description": "The slot index",
                  "type": "integer",
                  "minimum": 0,
                  "maximum": 35
                },
                "id": {
                  "description": "The item id",
                  "type": "integer"
                },
                "count": {
                  "description": "The item count",
                  "type": "integer",
                  "minimum": 0
                }
              }
            }
          },
          "main_hand": {
            "description": "The main hand selected slot index",
            "type": "integer",
            "minimum": 0,
            "maximum": 8
          }
        }
      }
    }
  }
}
```