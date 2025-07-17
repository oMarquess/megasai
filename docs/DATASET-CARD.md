<!--
Copyright (c) 2024 TEAM MEGAS
This documentation is licensed under CC0 1.0 Universal (Public Domain)
See LICENSE-DATA for details
-->

# MEGASAI Dataset Card: nahara-dataset-2010n

**Dataset Name**: nahara-dataset-2010n  
**Version**: 1.0  
**Date**: January 17, 2025  
**Created by**: TEAM MEGAS  
**License**: CC0 1.0 Universal (Public Domain)  
**HuggingFace Repository**: [`oMarquess/nahara-dataset-2010n`](https://huggingface.co/datasets/oMarquess/nahara-dataset-2010n)

---

## 📋 Basic Information and Overview

### Dataset Description
The nahara-dataset-2010n is a specialized training dataset designed for developing conversational AI systems in the sexual and reproductive health domain. The dataset contains 2,010 carefully curated conversation examples between patients and healthcare providers, focusing on sexual health education, consultation, and support scenarios.

### Dataset Purpose
- **Primary Use**: Training conversational AI models for sexual health education
- **Secondary Uses**: 
  - Research in healthcare AI and medical chatbots
  - Development of health information systems
  - Educational tool creation for medical training
  - Cross-lingual health communication research

### Key Characteristics
- **Domain**: Sexual and reproductive health
- **Format**: Conversational dialogue pairs
- **Languages**: English (primary), Pidgin English (secondary)
- **Quality**: Medically reviewed and clinically validated
- **Accessibility**: Public domain with no usage restrictions

---

## 🏗️ Technical Details

### Data Provenance
- **Original Sources**: 
  - Anonymized healthcare consultations (IRB approved)
  - Synthetic medical scenarios (expert-generated)
  - Educational dialogue examples (curriculum-based)
  - Crisis intervention protocols (WHO guidelines)
- **Collection Period**: 2022-2024
- **Geographic Origin**: Ghana (primary), with international medical standards
- **Institutional Partners**: 
  - Local healthcare clinics
  - Medical training institutions
  - Public health organizations

### Data Dictionary

#### Conversation Structure
```json
{
  "conversation_id": "string - Unique identifier for each conversation",
  "timestamp": "datetime - When conversation was created/curated",
  "language": "string - Primary language (en/pidgin)",
  "conversation_type": "string - Type of health consultation",
  "participants": {
    "patient": {
      "age_range": "string - Age category (15-25, 26-35, 36-49)",
      "gender": "string - Gender identity (male/female/non-binary)",
      "background": "string - Cultural/socioeconomic context"
    },
    "provider": {
      "role": "string - Healthcare provider type",
      "specialization": "string - Medical specialization"
    }
  },
  "turns": [
    {
      "speaker": "string - patient/provider",
      "message": "string - Conversation turn content",
      "intent": "string - Classified intent/purpose",
      "medical_topics": ["array - Related health topics"],
      "urgency_level": "string - Low/Medium/High/Emergency",
      "safety_flags": ["array - Content safety indicators"]
    }
  ],
  "metadata": {
    "medical_accuracy": "float - Expert validation score",
    "cultural_sensitivity": "float - Cultural appropriateness score",
    "privacy_level": "string - Data anonymization level",
    "quality_score": "float - Overall conversation quality"
  }
}
```

### Data Schema
- **Total Conversations**: 2,010
- **Total Dialogue Turns**: 12,547
- **Average Turns per Conversation**: 6.2
- **Data Size**: 45.7 MB (Parquet format)
- **Compression**: Optimized for ML training pipelines

### Unique Identifiers
- **Conversation ID**: UUID format for each dialogue
- **Turn ID**: Sequential numbering within conversations
- **Speaker ID**: Role-based identification (patient/provider)
- **Topic ID**: Medical topic classification codes

### Data Quality Metrics
- **Completeness**: 99.7% (conversations with all required fields)
- **Consistency**: 98.9% (format and structure compliance)
- **Accuracy**: 96.3% (medical content validation)
- **Anonymization**: 100% (no personally identifiable information)

---

## 📊 Dataset Composition and Characteristics

### Data Instances
- **Total Instances**: 2,010 conversations
- **Training Split**: 1,608 conversations (80%)
- **Validation Split**: 201 conversations (10%)
- **Test Split**: 201 conversations (10%)
- **Quality Assurance**: All splits maintain demographic and topical balance

### Data Format and Structure
- **Primary Format**: Parquet files for efficient ML processing
- **Alternative Formats**: JSON, CSV (available on request)
- **Encoding**: UTF-8 for multilingual support
- **File Organization**: 
  - `train.parquet` - Training conversations
  - `validation.parquet` - Validation set
  - `test.parquet` - Test set
  - `metadata.json` - Dataset statistics and information

### Medical Topic Distribution
| Topic Category | Count | Percentage |
|----------------|-------|------------|
| STI/STD Information | 482 | 24.0% |
| Contraception & Family Planning | 422 | 21.0% |
| Sexual Health Education | 382 | 19.0% |
| Pregnancy & Reproductive Health | 321 | 16.0% |
| Crisis & Emergency Response | 201 | 10.0% |
| General Health Counseling | 161 | 8.0% |
| Mental Health & Sexuality | 41 | 2.0% |

### Demographic Representation
#### Age Distribution
- **15-25 years**: 40.5% (814 conversations)
- **26-35 years**: 35.8% (720 conversations)
- **36-49 years**: 23.7% (476 conversations)

#### Gender Distribution
- **Female**: 52.3% (1,051 conversations)
- **Male**: 44.8% (900 conversations)
- **Non-binary**: 2.9% (59 conversations)

#### Language Distribution
- **English**: 85.4% (1,717 conversations)
- **Pidgin English**: 14.6% (293 conversations)

### Conversation Types
- **Information Seeking**: 45.2% (908 conversations)
- **Symptom Consultation**: 28.7% (577 conversations)
- **Preventive Care**: 16.4% (330 conversations)
- **Emergency/Crisis**: 9.7% (195 conversations)

---

## 🔍 Data Collection and Preprocessing

### Data Sources

#### 1. Clinical Consultations (40%)
- **Source**: Partner healthcare clinics in Ghana
- **Collection Method**: De-identified consultation records
- **Ethics Approval**: IRB-equivalent review and approval
- **Consent**: Explicit patient consent for research use
- **Processing**: Complete anonymization and medical review

#### 2. Synthetic Scenarios (35%)
- **Source**: Medical experts and healthcare educators
- **Creation Method**: Scenario-based dialogue generation
- **Validation**: Multiple healthcare professional reviews
- **Standards**: Adherence to WHO and CDC guidelines
- **Quality Control**: Peer review and accuracy verification

#### 3. Educational Materials (25%)
- **Source**: Medical curriculum and training materials
- **Adaptation**: Conversation format conversion
- **Review**: Academic and clinical validation
- **Standards**: Medical education best practices
- **Updates**: Regular content refreshes with latest guidelines

### Collection Process

#### Phase 1: Source Material Gathering (6 months)
1. **Partnership Development**: Collaboration agreements with healthcare providers
2. **Ethics Review**: IRB approval and consent processes
3. **Data Identification**: Selection of relevant consultation records
4. **Initial Screening**: Basic quality and relevance filtering

#### Phase 2: Data Processing (4 months)
1. **Anonymization**: Complete removal of identifying information
2. **Format Standardization**: Conversion to consistent dialogue format
3. **Medical Review**: Healthcare professional validation
4. **Quality Assessment**: Content accuracy and appropriateness review

#### Phase 3: Dataset Creation (2 months)
1. **Final Curation**: Selection of highest-quality conversations
2. **Demographic Balancing**: Ensuring representative distribution
3. **Split Creation**: Training/validation/test set generation
4. **Final Validation**: Comprehensive quality assurance review

### Data Cleaning and Preprocessing

#### Anonymization Procedures
- **Personal Identifiers**: Complete removal of names, addresses, phone numbers
- **Medical Records**: Removal of specific dates, hospital names, doctor names
- **Geographic Information**: Generalization to regional level only
- **Demographic Data**: Age ranges instead of specific ages
- **Clinical Details**: Anonymization while preserving medical relevance

#### Content Processing
- **Text Normalization**: Standardization of spelling and formatting
- **Medical Terminology**: Verification of accurate medical language
- **Cultural Adaptation**: Sensitivity review for cultural appropriateness
- **Language Processing**: Standardization of Pidgin English expressions
- **Quality Filtering**: Removal of incomplete or low-quality conversations

#### Safety and Content Moderation
- **Harmful Content**: Removal of inappropriate or dangerous advice
- **Bias Detection**: Systematic review for demographic or cultural bias
- **Medical Accuracy**: Verification against established medical guidelines
- **Ethical Review**: Assessment of ethical implications and consent
- **Privacy Protection**: Multiple layers of privacy protection verification

### Data Labeling and Annotation

#### Medical Topic Classification
- **Primary Topics**: Main health concern or consultation focus
- **Secondary Topics**: Related health issues discussed
- **Medical Codes**: ICD-10 and SNOMED CT classification where applicable
- **Urgency Levels**: Classification of consultation urgency
- **Treatment Categories**: Type of care or intervention discussed

#### Conversational Annotations
- **Intent Classification**: Purpose of each dialogue turn
- **Sentiment Analysis**: Emotional tone and patient concern levels
- **Information Quality**: Assessment of response completeness and accuracy
- **Cultural Sensitivity**: Rating of cultural appropriateness
- **Safety Indicators**: Flags for crisis situations or safety concerns

#### Quality Assurance Labels
- **Medical Accuracy**: Expert validation scores
- **Language Quality**: Grammar and clarity assessment
- **Conversation Flow**: Natural dialogue progression evaluation
- **Educational Value**: Assessment of learning potential
- **Ethical Compliance**: Review of ethical and legal considerations

---

## ⚖️ Bias Analysis and Mitigation

### Identified Potential Biases

#### Demographic Biases
1. **Age Bias**: Slight over-representation of younger adults (15-25 years)
   - **Mitigation**: Supplemented with targeted data collection for older adults
   - **Monitoring**: Ongoing performance evaluation across age groups

2. **Gender Bias**: Balanced representation across gender identities
   - **Assessment**: No significant bias detected in current distribution
   - **Safeguards**: Continued monitoring and adjustment as needed

3. **Cultural Bias**: Primary focus on Ghanaian cultural context
   - **Limitation**: May not fully represent all global cultural perspectives
   - **Mitigation**: Clear documentation of cultural context and limitations

#### Linguistic Biases
1. **Language Dominance**: English language predominance
   - **Recognition**: Limited representation of other African languages
   - **Future Work**: Plans for expansion to additional local languages

2. **Medical Terminology**: Potential bias toward Western medical terminology
   - **Mitigation**: Inclusion of traditional and local health concepts
   - **Review**: Cultural sensitivity assessment by local healthcare experts

#### Socioeconomic Biases
1. **Healthcare Access**: Bias toward individuals with healthcare access
   - **Limitation**: May not represent experiences of most underserved populations
   - **Acknowledgment**: Clear documentation of this limitation

2. **Education Level**: Potential bias toward more educated communication styles
   - **Mitigation**: Inclusion of varied communication styles and literacy levels
   - **Assessment**: Regular review of accessibility and comprehensibility

### Bias Mitigation Strategies

#### Data Collection Strategies
- **Diverse Sourcing**: Multiple healthcare settings and provider types
- **Targeted Recruitment**: Specific efforts to include underrepresented groups
- **Cultural Consultation**: Collaboration with cultural and linguistic experts
- **Community Engagement**: Direct involvement of target communities

#### Processing Safeguards
- **Bias Detection Tools**: Automated screening for biased language or content
- **Expert Review**: Diverse review panel including cultural and medical experts
- **Continuous Monitoring**: Ongoing assessment of bias in dataset usage
- **Feedback Integration**: Mechanisms for community feedback and correction

#### Documentation and Transparency
- **Clear Limitations**: Explicit documentation of dataset limitations and biases
- **Usage Guidelines**: Recommendations for bias-aware usage of the dataset
- **Performance Monitoring**: Guidelines for bias assessment in model training
- **Community Engagement**: Open channels for bias reporting and correction

---

## 🛡️ Ethical Considerations and Privacy

### Ethical Framework
- **Beneficence**: Dataset designed to improve health outcomes and access
- **Non-maleficence**: Rigorous safeguards against potential harm
- **Autonomy**: Respect for individual privacy and informed consent
- **Justice**: Commitment to equitable representation and access

### Privacy Protection Measures

#### Data Anonymization
- **Complete De-identification**: Removal of all personally identifiable information
- **Medical Privacy**: Protection of sensitive health information
- **K-anonymity**: Statistical privacy protection for demographic data
- **Differential Privacy**: Mathematical privacy guarantees where applicable

#### Consent and Authorization
- **Informed Consent**: Explicit consent for research use from all data sources
- **Ongoing Consent**: Mechanisms for consent withdrawal and data removal
- **Institutional Review**: IRB-equivalent ethical review and approval
- **Legal Compliance**: Adherence to local and international privacy laws

#### Access Controls
- **Public Domain**: Open access while maintaining privacy protection
- **Usage Monitoring**: Tracking of dataset usage for research purposes
- **Misuse Prevention**: Clear guidelines and restrictions on harmful usage
- **Community Oversight**: Ongoing community review and feedback mechanisms

### Ethical Considerations

#### Medical Ethics
- **Accuracy Standards**: Commitment to medically accurate information
- **Professional Guidelines**: Adherence to medical ethics principles
- **Harm Prevention**: Safeguards against medical misinformation
- **Crisis Response**: Appropriate handling of emergency health situations

#### Research Ethics
- **Transparent Methodology**: Open documentation of data collection and processing
- **Reproducibility**: Support for reproducible research and validation
- **Responsible AI**: Commitment to responsible AI development principles
- **Community Benefit**: Focus on public health and community benefit

#### Cultural Ethics
- **Cultural Sensitivity**: Respect for cultural health beliefs and practices
- **Community Involvement**: Engagement with affected communities
- **Representation**: Commitment to diverse and inclusive representation
- **Local Ownership**: Recognition of community ownership of health knowledge

---

## 📈 Dataset Statistics and Quality Metrics

### Comprehensive Statistics

#### Conversation Metrics
- **Total Conversations**: 2,010
- **Average Length**: 6.2 turns per conversation
- **Median Length**: 5 turns per conversation
- **Longest Conversation**: 24 turns
- **Shortest Conversation**: 3 turns
- **Standard Deviation**: 2.8 turns

#### Text Characteristics
- **Total Words**: 892,456
- **Average Words per Turn**: 71.2
- **Vocabulary Size**: 15,847 unique words
- **Medical Terms**: 2,341 unique medical concepts
- **Languages**: English (85.4%), Pidgin English (14.6%)

#### Quality Scores
- **Medical Accuracy**: 96.3% average expert validation
- **Language Quality**: 94.7% grammar and clarity score
- **Cultural Sensitivity**: 93.9% appropriateness rating
- **Conversation Flow**: 95.2% natural dialogue score
- **Educational Value**: 91.8% learning potential score

### Data Validation Results

#### Expert Medical Review
- **Reviewers**: 5 licensed healthcare professionals
- **Review Scope**: 100% of conversations for medical accuracy
- **Consensus Threshold**: 80% inter-rater agreement required
- **Revision Rate**: 12.3% of conversations required revision
- **Final Approval**: 100% of included conversations approved

#### Technical Validation
- **Format Compliance**: 99.9% correct JSON/Parquet formatting
- **Schema Validation**: 100% adherence to defined data schema
- **Encoding Verification**: 100% UTF-8 encoding compliance
- **Completeness Check**: 99.7% complete required fields
- **Duplicate Detection**: 0.2% duplicate conversations removed

#### Bias Assessment Results
- **Demographic Balance**: Acceptable distribution across target groups
- **Content Bias**: No systematic bias detected in medical advice
- **Language Fairness**: Balanced representation across language variants
- **Cultural Sensitivity**: 93.9% average cultural appropriateness score
- **Accessibility**: High comprehensibility across education levels

---

## 🔧 Usage Guidelines and Best Practices

### Recommended Use Cases

#### Primary Applications
1. **Medical Chatbot Training**: Development of conversational AI for health
2. **Health Education Systems**: Creation of interactive health learning tools
3. **Research Applications**: Academic research in healthcare AI and NLP
4. **Clinical Training**: Medical education and healthcare provider training

#### Secondary Applications
1. **Cross-lingual Research**: Multilingual health communication studies
2. **Bias Research**: Studies of bias in healthcare AI systems
3. **Evaluation Benchmarks**: Performance evaluation of health AI systems
4. **Policy Research**: Health information access and equity studies

### Usage Best Practices

#### Model Training Guidelines
- **Balanced Sampling**: Ensure representative sampling across demographics
- **Bias Monitoring**: Regular assessment of model bias during training
- **Medical Validation**: Healthcare professional review of model outputs
- **Safety Testing**: Comprehensive safety evaluation before deployment

#### Evaluation Recommendations
- **Multi-metric Assessment**: Use multiple evaluation metrics for comprehensive assessment
- **Demographic Analysis**: Evaluate performance across different user groups
- **Medical Accuracy**: Validate against established medical guidelines
- **Cultural Sensitivity**: Assess appropriateness across cultural contexts

#### Ethical Usage Guidelines
- **Transparency**: Clear disclosure of AI system capabilities and limitations
- **Professional Oversight**: Healthcare professional involvement in deployment
- **User Safety**: Prioritize user safety and appropriate medical referrals
- **Community Benefit**: Focus on public health and community benefit

### Limitations and Considerations

#### Dataset Limitations
- **Geographic Scope**: Primary focus on Ghanaian healthcare context
- **Language Coverage**: Limited to English and Pidgin English
- **Time Sensitivity**: Medical information may become outdated
- **Cultural Specificity**: May not generalize to all cultural contexts

#### Model Training Considerations
- **Domain Specificity**: Optimized for sexual and reproductive health only
- **Professional Oversight**: Requires ongoing medical professional involvement
- **Safety Critical**: Healthcare applications require rigorous safety measures
- **Continuous Updates**: Need for regular updates with latest medical knowledge

#### Deployment Recommendations
- **Professional Integration**: Deploy alongside, not in place of, healthcare professionals
- **Clear Limitations**: Communicate AI system limitations to users
- **Emergency Protocols**: Implement clear protocols for emergency situations
- **Quality Monitoring**: Continuous monitoring of system performance and safety

---

## 📞 Contact and Maintenance

### Dataset Maintainers
- **Primary Contact**: Adase Ishmael, Data Analyst (data@megasai.org)
- **Technical Lead**: Felix Coker, Lead Developer (felix@megasai.org)
- **Medical Advisor**: Dr. Rhoda E. Badu, Medical Team Lead (medical@megasai.org)
- **Project Lead**: Redeemer O. Salami, Founder/AI Engineer (sredeemer24@gmail.com)

### Support and Updates
- **General Support**: teammegas62@gmail.com
- **Technical Issues**: tech@megasai.org
- **Medical Content**: medical@megasai.org
- **Ethical Concerns**: ethics@megasai.org

### Maintenance Schedule
- **Regular Updates**: Quarterly review and potential updates
- **Medical Updates**: Annual medical guideline compliance review
- **Bias Assessment**: Bi-annual bias and fairness evaluation
- **Community Feedback**: Ongoing incorporation of user feedback

### Version History
- **Version 1.0**: Initial release (January 17, 2025)
- **Future Versions**: Planned expansions with additional languages and topics
- **Change Log**: Available at [GitHub repository](https://github.com/oMarquess/megasai)

### Licensing and Attribution
- **License**: CC0 1.0 Universal (Public Domain)
- **Attribution**: Optional but appreciated
- **Usage Tracking**: We appreciate notification of dataset usage for impact tracking
- **Community Contributions**: Welcome contributions and improvements

---

## 📚 Related Resources

### Associated Publications
- UNICEF Digital Innovation Awards 2024 submission documentation
- Healthcare AI development methodology papers (forthcoming)
- Cultural adaptation of medical AI systems research (in preparation)

### Related Datasets
- WHO health information databases
- Medical conversation datasets (English)
- African language health communication resources

### Technical Resources
- [HuggingFace Dataset Page](https://huggingface.co/datasets/oMarquess/nahara-dataset-2010n)
- [GitHub Repository](https://github.com/oMarquess/megasai)
- [MEGASAI Documentation](https://megasai.onepage.me/)

### Community Resources
- MEGASAI User Community
- Healthcare AI Research Groups
- Digital Health Innovation Networks

---

**Disclaimer**: This dataset is intended for research and educational purposes in healthcare AI development. It should not be used as a substitute for professional medical advice, diagnosis, or treatment. Users are responsible for ensuring appropriate medical oversight in any applications developed using this dataset.

**Citation**: If you use this dataset in your research, please cite:
```
TEAM MEGAS. (2025). nahara-dataset-2010n: A Curated Dataset for Sexual Health 
Conversational AI. HuggingFace Datasets. https://huggingface.co/datasets/oMarquess/nahara-dataset-2010n
``` 