# Interface Spec


## Illustrative JSON
```json
{
    "schema_version": "0.1-draft",
    "sketch_id": "sketch_A",
    "elements": [{"id": "line_1", "type": "line"}],
    "dimensions": [{"id": "dim_1", "element_refs": ["line_1"],
    "kind": "length", "value": 25.0, "unit": "mm"}],
    "constraints": [{"id": "con_1", "element_refs": ["line_1"],
    "kind": "horizontal", "status": "unknown"}],
    "sketch_status": "unknown"
}
```

## Possible JSON
I need part file to see can the pyCATIA extract (Constraints)
```json
{
    "catia_v": version, //check if catia is the correct version
    "sketch_id": id, // file name or part name?
    "elements": [{"id": "line_1", "type": "line"}], 
    "dimensions": [{"id": "dim_1", "element_refs": ["line_1"],
    "kind": "length", "value": 25.0, "unit": "mm"}],
    "constraints": [{"id": "con_1", "element_refs": ["line_1"],
    "kind": "horizontal", "status": "unknown"}],
}
```

pycatia_script (https://github.com/KaiUR/Pycatia_Scripts):
- A collection of PyCATIA script useful!
- Dependencies: pycatia, wxPython, xlsxwriter

## PyCATIA Library and its important class:
pycatia.base_interfaces.context (https://pycatia.readthedocs.io/en/latest/api/pycatia/base_interfaces/context.html)
- For open CATIA Document and part

pycatia.mec_mod_interfaces.part (https://pycatia.readthedocs.io/en/latest/api/pycatia/mec_mod_interfaces/part.html#part)
- Access the part
- Contain property **Constraints**

### Constraints
- https://pycatia.readthedocs.io/en/latest/api/pycatia/mec_mod_interfaces/constraints.html#pycatia.mec_mod_interfaces.constraints.Constraints
- item(i_index: int | str) -> Constraints. Return constraints based on index of part or name
- **Consider the order (index) and the name of the part**
- Most important class. We need this to see the constraint of the part