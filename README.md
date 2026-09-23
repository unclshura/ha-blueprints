# Homeassistant reusable blueprints

## sync-switches.yaml - **Blueprint: Master Physical Switch + Multiple Logical Slaves (No Smart Ceiling Light)**

- SW1’s *state* is the **only truth** about the ceiling light.
- There is **no ceiling light entity** in Home Assistant.
- Slave indicators must mirror **SW1’s state**, not a light entity.
- Slave presses must **toggle SW1**, and then indicators update.


### **Behaviour**
- **Master switch (SW1)**  
  - Physical, wired to dumb ceiling light  
  - Its state is the truth  
  - All slave indicators mirror SW1

- **Slave switches (SW2, SW3, …)**  
  - Logical buttons  
  - When pressed → invert SW1  
  - Their indicators mirror SW1

- **Lock boolean**  
  - Prevents recursion when SW1 toggles indicators or slaves toggle SW1
