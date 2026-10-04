# Use Case Scenarios — TCMS

> Status: Draft — Based on aim45an diagrams (2026-10-04)
> Author: أيمن عبد الوهاب (aim45an)
> Pending: Doctor's template confirmation

## 1. Actors (8)

| ID | Actor | Arabic | Role |
|----|-------|--------|------|
| A-01 | Super Admin | المشرف العام | Full system access |
| A-02 | Company Admin | مدير الشركة | Company-level management |
| A-03 | Branch Manager | مدير الفرع | Branch-level management |
| A-04 | Customer Service | موظف خدمة العملاء | Customer operations |
| A-05 | Customer | العميل | End user (self-service + own data) |
| A-06 | Accountant | المحاسب | Billing & payments |
| A-07 | Network Engineer | مهندس الشبكة | Network infrastructure |
| A-08 | Support Agent | موظف الدعم الفني | Ticket handling |

## 2. Modules (12)

| ID | Module | Arabic |
|----|--------|--------|
| M1 | Identity Service | خدمة الهوية والوصول |
| M2 | Customer Service | خدمة العملاء |
| M3 | SIM & Number Service | الشرائح والأرقام |
| M4 | Product / Package Service | المنتجات والباقات |
| M5 | Subscription Service | الاشتراكات |
| M6 | Usage Service | شحن الاستهلاك |
| M7 | Billing Service | الفواتير والاحصاء |
| M8 | Payment Service | المدفوعات |
| M9 | Network Service | الشبكة |
| M10 | Incident Service | الأعطال |
| M11 | Support Service | الدعم الفني |
| M12 | End-to-End | دورة العمل الكاملة |

## 3. Use Cases (42)

### M1 — Identity Service
- UC-01: Login / تسجيل الدخول
- UC-02: Logout / تسجيل الخروج
- UC-03: Register User / إنشاء مستخدم
- UC-04: Refresh Token / تحديث التوكن

### M2 — Customer Service
- UC-05: Create Customer / إنشاء عميل
- UC-06: Update Customer / تحديث بيانات عميل
- UC-07: Delete Customer / حذف عميل
- UC-08: List Customers / عرض قائمة العملاء
- UC-09: View Customer Details / عرض تفاصيل عميل
- UC-01V: Verify National ID / التحقق من الرقم الوطني

### M3 — SIM & Number Service
- UC-10: Create SIM / إنشاء شريحة
- UC-11: Activate SIM / تفعيل الشريحة وتخصيصها
- UC-12: Suspend SIM / إيقاف شريحة
- UC-13: Block SIM / حظر شريحة
- UC-14: Assign Phone Number / تخصيص رقم هاتف

### M4 — Product / Package Service
- UC-15: Create Package / إنشاء باقة
- UC-16: Update Package / تحديث باقة
- UC-17: Delete Package / حذف باقة
- UC-18: List Packages / عرض الباقات

### M5 — Subscription Service
- UC-19: Create Subscription / إنشاء اشتراك
- UC-20: Renew Subscription / تجديد اشتراك
- UC-21: Cancel Subscription / إلغاء اشتراك

### M6 — Usage Service
- UC-22: Record Call / تسجيل مكالمة
- UC-23: Record Message / تسجيل رسالة
- UC-24: Record Internet Usage / تسجيل استهلاك

### M7 — Billing Service
- UC-25: Generate Invoice / إصدار فاتورة
- UC-26: Calculate Amounts / حساب المبالغ
- UC-27: Update Payment Status / تحديث حالة الدفع

### M8 — Payment Service
- UC-28: Process Payment / تنفيذ عملية الدفع
- UC-29: Recharge Balance / شحن رصيد
- UC-30: Check Transaction Status / حالة العملية

### M9 — Network Service
- UC-31: Manage Towers / إدارة الأبراج
- UC-32: Manage Stations / إدارة المحطات
- UC-33: Manage Devices / إدارة الأجهزة
- UC-34: Manage Coverage Areas / إدارة مناطق التغطية

### M10 — Incident Service
- UC-35: Report Incident / تسجيل بلاغ عطل
- UC-36: Assign Incident to Tower / ربط العطل بالبرج
- UC-37: Track Incident / متابعة العطل

### M11 — Support Service
- UC-38: Create Ticket / إنشاء تذكرة شكوى
- UC-39: Assign Ticket / إسناد التذكرة
- UC-40: Reply to Ticket / الرد على التذكرة
- UC-41: Transfer Ticket / تحويل التذكرة

### M12 — End-to-End
- UC-42: Full Customer Lifecycle / دورة العميل الكاملة

## 4. Use Case Diagram

See: docs/diagrams/phase-2-use-cases/01-use-case-overview.drawio (+ PNG)
Related: docs/diagrams/phase-2-use-cases/02-use-case-customer-lifecycle.drawio, docs/diagrams/phase-2-use-cases/03-use-case-network-support.drawio

## 5. Open Questions

- [ ] OQ-06: Doctor's approval of actor list?
- [ ] Doctor's Use Case template?
- [ ] Level of detail for each UC?
