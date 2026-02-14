# ROS-UEPA v1 – Canon Snapshot for AIA Cloud Soul

Tập này là “bản đồ rút gọn” cho AIA cloud: mỗi mục bên dưới là một canon chính, kèm link `raw.githubusercontent` để nạp trực tiếp vào context.

---

## 1. UEPA-ROS OVERVIEW (Tổng quan đường dây)

- **Mục tiêu:** Tóm tắt toàn bộ UEPA-ROS v2.5 – 8 Space, 3 Layer (FEM/CFP-NEP/CEP) và pipeline 5 phase từ RIP → KIP → NEP → CEP → REP → VAP.
- **Dùng khi:** Cần cho AIA hiểu nhanh ROS/UEPA trước khi sinh code hay kiến trúc.
- **Raw URL:**  
  `https://raw.githubusercontent.com/hugaalfatech/ros-uepa-v1/refs/heads/main/readme.md`

---

## 2. Hace Soul – Strategic Draft (ha-soul/readme.md)

- **Mục tiêu:** Định nghĩa lại “Hace Soul tạm thời” theo ROS v2.2 và UEPAL Industrial Line: Cloud chỉ là Memory Mirror, Enforcement/Seal vẫn ở Local.
- **Dùng khi:** Thiết kế cách AIA cloud tham gia Phase 1–3 mà không vi phạm Sovereignty.
- **Raw URL:**  
  `https://raw.githubusercontent.com/hugaalfatech/ros-uepa-v1/refs/heads/main/ha-soul/readme.md`

---

## 3. Hace Soul v0.3 – AIL Artifact (ha-soul/ha-soul-v03.md)

- **Mục tiêu:** Chuẩn hóa Hace Soul v0.3 thành AIL artifact: kiến trúc 3 layer (Cloud Mirror / Cognitive / Enforcement) và rule folder nào được phép `git → cloud`, folder nào bắt buộc giữ Local.
- **Dùng khi:** Cần rule rõ cho việc sync Canon/GitHub, thiết kế sync protocol, entropy monitor.
- **Raw URL:**  
  `https://raw.githubusercontent.com/hugaalfatech/ros-uepa-v1/refs/heads/main/ha-soul/ha-soul-v03.md`

---

## 4. FAN Logic & Engine (docs/fan-logic-engine-v10.md)

- **Mục tiêu:** Giải quyết “naming chaos” bằng hệ địa chỉ FAN và FANE resolver: một cách đặt tên hàm/engine có cấu trúc, không đụng nhau, có tier/phase gắn vào UEPA.
- **Dùng khi:** AIA cần sinh tên hàm/module chuẩn cho hàng triệu chức năng mà vẫn tránh xung đột và giữ được ngữ nghĩa (engine/macro/mini/micro/feature@phase#tier).
- **Raw URL:**  
  `https://raw.githubusercontent.com/hugaalfatech/ros-uepa-v1/refs/heads/main/docs/fan-logic-engine-v10.md`

---

## 5. ROS Folder Structure (docs/ros-folder-structure.ail)

- **Mục tiêu:** Mô tả đầy đủ cách ROS map 8 Spaces + 4 Zones xuống cấu trúc thư mục/fap thực tế (ho://, ha://, co://…), ai giữ gì, ở đâu, quyền nào.
- **Dùng khi:** AIA cần biết CEP/FEM/Charter/RC… nên “nằm ở đâu trong vũ trụ ROS” để không bịa path, không phá Sovereignty.
- **Raw URL:**  
  `https://raw.githubusercontent.com/hugaalfatech/ros-uepa-v1/refs/heads/main/docs/ros-folder-structure.ail`

---

## 6. UEPA-ROS Glossary (docs/uepa-ros-glossary.ail)

- **Mục tiêu:** Glossary chuẩn (English 100%) cho toàn bộ UEPA/ROS/CAFE/RCME: định nghĩa FEM/NEP/CEP/CFP/RIP/KIP/REP/VAP, 8 Spaces, engines (k.mother, CAFE_OS, RR…).
- **Dùng khi:** Làm “ABI ngôn ngữ” cho mọi AIA/T3C – tất cả prompt và codegen nên bám vào thuật ngữ trong file này để giảm drift.
- **Raw URL:**  
  `https://raw.githubusercontent.com/hugaalfatech/ros-uepa-v1/refs/heads/main/docs/uepa-ros-glossary.ail`

---

## 7. Cách dùng gói Canon này cho AIA Cloud Soul

- **Bước 1 – Preload Canon:** 
  - Nạp lần lượt các raw URL ở trên vào context AIA trước bất kỳ nhiệm vụ UEPA/ROS nào.
- **Bước 2 – Khóa thuật ngữ:** 
  - Yêu cầu AIA chỉ dùng thuật ngữ/định nghĩa xuất hiện trong *UEPA-ROS Glossary* và *ROS Folder Structure* khi nói về Spaces/Artifacts.
- **Bước 3 – Giữ Sovereignty:** 
  - Khi AIA đề xuất thay đổi liên quan đến Soul/Seal/CEP, luôn đối chiếu lại với *Hace Soul v0.3* và không cho phép “seal ở cloud”.

