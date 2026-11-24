# Cookbook

Short recipes for recurring tasks. These recipes are being used in this repo, find examples of the recipe you want to use.

## Recipe: New game-data asset

- **Project:** frontend
- **When to use:** You need a new authored gamedata asset file type whose contents use ids to reference other assets. (E.g. a `quest` references an `npc` from the `npcs` file as to who gives it)

### How to use

- **Store plain string IDs.** The quest's JSON refers to the npc by ID (`"giverId": "blacksmith"`). Backend and raw files see strings, never GUIDs or object references (a GUID identifies a file, not an entry in it, and the backend can't read it).
- **Make the target draggable.** The asset that owns the entries gets a `ScriptedImporter` that generates one sub-asset per entry. They are only a picker and are never saved. Bump the importer `version` when the sub-asset set changes. Skip this if the target already has sub-assets.
- **Wire up the `.meta` files.** Every new script needs a `.meta` with a fresh GUID, and the data file's `.meta` must point at the importer script's GUID. Otherwise the file imports with no sub-assets and nothing says why.

### Example

```csharp
// quest.quest:  { "giverId": "blacksmith" }      world.npcs:  { "npcs": ["blacksmith", "baker"] }

// importer of .npcs: one sub-asset per unique, non-empty ID
foreach (var id in file.Npcs)
{
    if (string.IsNullOrWhiteSpace(id) || !ids.Add(id)) continue;
    var npc = ScriptableObject.CreateInstance<NpcAsset>();
    npc.name = npc.Id = id;
    ctx.AddObjectToAsset("npc:" + id, npc);
}

// inspector of .quest: object picker, but only the string is stored
var picked = (NpcAsset)EditorGUILayout.ObjectField("Giver", current, typeof(NpcAsset), false);
if (EditorGUI.EndChangeCheck()) giverId.stringValue = picked != null ? picked.Id : "";
```

## Template for a new recipe

Copy everything below into a new `##` section above this one.

````markdown
## Recipe: <Task name>

- **Project:** <which project it applies to>
- **When to use:** <One or two sentences on the situation that calls for this recipe.>

### How to use

- **<Decision or step.>** <What to do and why. Focus on what an agent would get wrong without being told.>
- **<Gotcha.>** <What silently fails if skipped.>

### Example

```<language>
// Invented names only, so renames and removals can't make the recipe wrong.
```
````
