## Material Selection and Load Cell Integration

### Objective
Select the most suitable material and construction method for building smart parallettes equipped with load cells, balancing ease of build, aesthetics, electronics integration, and functionality.

---

### Comparison: PVC vs. Wood

| Criteria                          | **PVC Parallettes**                                                                                           | **Wooden Parallettes**                                                                                     |
|----------------------------------|---------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| **Ease of Construction**         | ✅ Very easy to cut, assemble, and glue                                                                      | ⚠️ Requires drilling, screwing, and possibly woodworking skills                                             |
| **Material Cost**                | ✅ Low cost for pipes and joints (~10–15€)                                                                    | ✅ Even lower (basic timber pieces cost ~5–10€)                                                             |
| **Aesthetic Appeal**             | ✅ Modern, gym-like appearance (if well-finished)                                                              | ❌ Can look DIY or rough unless polished and painted                                                        |
| **Load Cell Mounting**           | ❌ Challenging due to rounded, hollow structure; may need 3D-printed or custom brackets                       | ✅ Flat surfaces ideal for mounting; wood screws directly into structure                                    |
| **Electronics Integration**      | ✅ Hollow structure allows internal routing of wires and housing of HX711/Arduino                            | ❌ Wires and electronics must be externally mounted or housed in a separate box                             |
| **Structural Strength**          | ⚠️ Sufficient for moderate load if PVC is thick enough; may flex under high load                              | ✅ Very sturdy and proven to hold full body weight during exercises                                         |
| **Modularity / Expandability**   | ✅ Can experiment with modular attachments and inner cabling                                                  | ⚠️ More rigid in form; harder to modify post-build                                                         |
| **Weight / Portability**         | ✅ Lightweight and portable                                                                                   | ❌ Heavier and bulkier                                                                                      |

---

### Load Cell Considerations

- Using **4 load cells per parallette**, one for each contact point (foot of the base).
- Load cells like [this model](https://de.aliexpress.com/item/1005007254273938.html) require a **rigid and flat mount**, as strain readings depend on proper deformation patterns.
- **Wooden base** can be drilled and used with bolts or screws, ensuring stable force transfer.
- **PVC base** would require a custom platform or 3D-printed mounts to hold the load cells flat, and to avoid flexing under pressure.

---

### Decision Summary

| Option        | Verdict       | Rationale |
|---------------|---------------|-----------|
| **PVC**       | ✅ *Promising, but more complex to integrate load cells* | Easiest to build and wire; will require creative mounting (3D print brackets or insert wood plates). Aesthetic and good for hiding electronics. |
| **Wood**      | ✅ *Technically easier for load cell accuracy* | Simpler and cheaper to mount load cells properly. May need external wire routing and some aesthetic improvements.|

---

### Examples and Inspiration
https://www.instructables.com/Wooden-Parallettes/ \
https://gmb.io/parallettes-construction/ \
https://www.instructables.com/PVC-Parallettes/ \
![Mixbars](https://github.com/user-attachments/assets/20626f42-2491-4c2d-8f5f-572a5a72dd5e)
![Woodbars](https://github.com/user-attachments/assets/16e15adf-95cb-4e9a-aa33-a4adb6acdf0f)
![pvcbars](https://github.com/user-attachments/assets/d6fd1e45-9c49-4bc0-a120-967a37d4844c)

---
### Next Steps

- Prototype both base types (small-scale or one parallette) to evaluate:
  - Load cell responsiveness and calibration ease
  - Wire routing and stability
- Optionally design 3D-printed brackets for PVC to hold the load cells securely
- Decide on final build material based on:
  - Quality of sensor data
  - Build effort vs. payoff
  - Visual and functional goals of the final device


