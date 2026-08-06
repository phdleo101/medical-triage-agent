# Medical Triage Agent

> An intelligent triage recommendation system built on Tencent Yuanqi platform, helping patients find the right department based on symptoms.

[![Live Demo](https://img.shields.io/badge/Demo-Tencent_Yuanqi-00C853?style=for-the-badge)](https://yuanqi.tencent.com/webim/#/chat/JcPxWB?appid=2084923057113837824&experience=true)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/phdleo101/medical-triage-agent)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)

## Overview

This project is an intelligent triage assistant that collects patient symptom information through multi-turn dialogue, assesses urgency levels, recommends appropriate departments, and provides visit guidance.

**Core Positioning**: Triage recommendation (not diagnosis), compliant with national health regulations.

## Features

- **Symptom Collection**: Multi-turn dialogue, patiently gathering symptom information
- **Urgency Assessment**: Red/Yellow/Green three-level alert, critical values prioritized for emergency
- **Department Recommendation**: 90+ symptoms precisely matched to departments
- **Visit Guidance**: Includes pre-visit preparation and health education
- **Compliance Design**: No diagnosis, no prescriptions, no doctor replacement

## Knowledge Base

| Knowledge Base | File | Content |
|---|---|---|
| Symptom-Department Mapping | `data/knowledge/symptom_department_mapping.md` | 90+ symptoms, 8 body regions |
| Emergency Symptom Recognition | `data/knowledge/emergency_symptoms.md` | Red/Yellow/Green levels, 10 critical categories |
| Disease Encyclopedia | `data/knowledge/disease_encyclopedia.md` | 50+ diseases with pre-visit guidance |

## Tech Stack

- **Platform**: Tencent Yuanqi (yuanqi.tencent.com)
- **Knowledge Base**: Markdown format, vector retrieval
- **Model**: Tencent Hunyuan LLM
- **Deployment**: Tencent Yuanqi web publishing

## Test Results

| Input | Urgency | Department | Possible Causes |
|---|---|---|---|
| Headache 3 days with nausea | Yellow | Neurology | Migraine / Tension headache / Hypertension |
| Severe chest pain 30min, cold sweats | Red | ER / Cardiology | Acute MI / Angina / Aortic dissection |
| 2yo child fever 39.5C, lethargic | Red | Pediatric ER | URI / HFMD / Pneumonia |
| BP 150/95 on checkup, occasional dizziness | Yellow | Cardiology | Hypertension / Cervical spondylosis |
| Vague abdominal pain | - | Bot asks follow-up questions | Multi-turn dialogue triggered |

## Compliance Statement

- This system provides triage recommendations only, not medical diagnosis or treatment advice
- No prescriptions, no specific medication recommendations
- Does not replace in-person medical consultation
- For emergencies, call 120 or go to ER immediately

## License

MIT
