# JK Flip-Flop Using NAND Gates

This project is a gate-level implementation of a JK flip-flop using only NAND gates, built and simulated in Logisim Evolution (v3.7.2).  
The idea was to understand how the JK flip-flop works internally, why it faces issues like the race around condition, and how a master-slave design solves those issues.  

All circuit files are in the folder `Circuit Files` and all simulation images are in the folder `Images`.

---

## JK Flip-Flop Basics

| J | K | Q (next state) | Description |
|---|---|----------------|-------------|
| 0 | 0 | Hold           | No change   |
| 0 | 1 | Reset          | Q = 0       |
| 1 | 0 | Set            | Q = 1       |
| 1 | 1 | Toggle         | Complement  |

---

## Race Around Problem
When both J and K are 1 with the clock high, the basic circuit oscillates due to feedback. To fix this, I used a master-slave design:
- Master operates on the rising edge  
- Slave operates on the falling edge  
- Prevents oscillations and ensures stable toggling  

---

## Simulation Results

Here are the captured outputs from Logisim under different input cases:

| Inputs (J,K,C) | Circuit Output |
|----------------|----------------|
| J=0, K=0, C=1 | Hold <img width="1920" height="1080" alt="J=0,K=0,C=1" src="https://github.com/user-attachments/assets/b696452d-464b-4d98-b94b-24bddbeed221" /> |
| J=0, K=1, C=1 | Reset <img width="1920" height="1080" alt="J=0,K=1,C=1" src="https://github.com/user-attachments/assets/fea97435-df0f-4d90-ac54-7a1068c3f668" /> |
| J=1, K=0, C=1 | Set <img width="1920" height="1080" alt="J=1,K=0,C=1" src="https://github.com/user-attachments/assets/83f5dcad-51e0-49fc-8243-3c17b5478a35" /> |
| J=1, K=1, C=1 | Toggle <img width="1920" height="1080" alt="J=1,K=1,C=1" src="https://github.com/user-attachments/assets/571ee43b-0685-4533-8c05-850ea775c966" /> |
| J=1, K=1, C=0 | Hold (clock low) <img width="1920" height="1080" alt="J=1,K=1,C=0" src="https://github.com/user-attachments/assets/c54b7052-d65d-48a8-81b5-fc9c0aab6ace" /> |
| J=1, K=1, C=1 (2nd toggle) | Toggle 2nd <img width="1920" height="1080" alt="J=1,K=1,C=1 (2ND)" src="https://github.com/user-attachments/assets/d191c820-6456-4c97-b13a-45e2210608c9" /> |


---

## Conclusion
Building this flip-flop from scratch gave me a better understanding of sequential logic and timing in digital systems. The master-slave configuration eliminated the race around problem, and the final circuit behaved exactly as expected.  

This circuit can be extended further for counters, registers, and more complex synchronous designs.  

---

### Files Included
- `Circuit Files` → Logisim `.circ` file  
- `Images` → Simulation outputs for each test case  
