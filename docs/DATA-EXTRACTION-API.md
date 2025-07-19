<!--
Copyright (c) 2024 TEAM MEGAS
This documentation is licensed under CC0 1.0 Universal (Public Domain)
See LICENSE-DATA for details
-->

# MEGASAI Data Extraction API Documentation

**Version**: 1.0  
**Last Updated**: January 17, 2025  
**API Base URL**: `https://api.megasai.org/v1`  
**Documentation Type**: Technical API Specification for Data Extraction

---

## 📋 Overview

This documentation provides comprehensive technical specifications for extracting data and content from the MEGASAI system. These APIs enable researchers, healthcare organizations, and developers to access anonymized data in compliance with privacy regulations and open data principles.

### Key Principles
- **Privacy-First**: Only non-personally identifiable information (non-PII) is extractable
- **Open Formats**: All data available in open, non-proprietary formats (JSON, CSV, XML)
- **Standards Compliance**: Follows FHIR, HL7, and OpenAPI 3.0 specifications
- **Rate Limited**: Reasonable usage limits to ensure system stability

---

## 🔧 Authentication

### API Key Authentication
```http
GET /api/v1/export/conversations
Authorization: Bearer {your_api_key}
Content-Type: application/json
```

### Obtaining API Keys
1. **Research/Academic Use**: Contact `teammegas62@gmail.com`
2. **Healthcare Organizations**: Contact `teammegas62@gmail.com`
3. **Public Health Agencies**: Contact `teammegas62@gmail.com`
4. **Developers**: Contact `teammegas62@gmail.com`

---

## 📊 Available Data Extraction Endpoints

### 1. Conversation Analytics Export

**Endpoint**: `GET /api/v1/export/conversations`

**Description**: Export anonymized conversation patterns and analytics data for research purposes.

**Parameters**:
```json
{
  "date_from": "2025-01-01",
  "date_to": "2025-01-17",
  "format": "json|csv|xml",
  "include_metadata": true,
  "language": "en|pidgin|all",
  "category": "general|sti|contraception|emergency|all"
}
```

**Response Example (JSON)**:
```json
{
  "metadata": {
    "export_date": "2025-01-17T10:30:00Z",
    "total_records": 1542,
    "date_range": {
      "from": "2025-01-01",
      "to": "2025-01-17"
    },
    "privacy_level": "non_pii_only"
  },
  "conversations": [
    {
      "conversation_id": "anonymous_conv_001",
      "timestamp": "2025-01-15T14:22:00Z",
      "category": "sti_information",
      "language": "en",
      "user_demographics": {
        "age_range": "20-25",
        "region": "west_africa",
        "gender": "not_specified"
      },
      "interaction_data": {
        "total_messages": 8,
        "session_duration_minutes": 12,
        "resolution_status": "information_provided",
        "satisfaction_rating": 4,
        "follow_up_needed": false
      },
      "content_analysis": {
        "topics_discussed": ["hiv_testing", "prevention_methods"],
        "resources_provided": ["testing_locations", "prevention_guide"],
        "emergency_level": "low",
        "referred_to_professional": false
      }
    }
  ]
}
```

### 2. Health Statistics Export

**Endpoint**: `GET /api/v1/export/health-statistics`

**Description**: Export aggregated health query statistics for public health analysis.

**Parameters**:
```json
{
  "aggregation_level": "daily|weekly|monthly",
  "geographic_scope": "global|region|country",
  "include_trends": true,
  "format": "json|csv"
}
```

**Response Example (JSON)**:
```json
{
  "statistics": {
    "period": "2025-01",
    "aggregation": "monthly",
    "geographic_scope": "global",
    "queries_by_category": {
      "sti_testing": {
        "total_queries": 1245,
        "unique_users": 987,
        "avg_session_duration": 8.5,
        "satisfaction_rate": 4.2
      },
      "contraception": {
        "total_queries": 892,
        "unique_users": 734,
        "avg_session_duration": 6.8,
        "satisfaction_rate": 4.5
      },
      "emergency_consultation": {
        "total_queries": 156,
        "unique_users": 156,
        "professional_referrals": 89,
        "avg_response_time_seconds": 45
      }
    },
    "trending_topics": [
      {
        "topic": "hiv_prep",
        "growth_rate": 15.2,
        "total_mentions": 234
      }
    ]
  }
}
```

### 3. Training Data Export

**Endpoint**: `GET /api/v1/export/training-data`

**Description**: Export curated training conversations for AI model development.

**Parameters**:
```json
{
  "dataset_version": "1.0",
  "format": "parquet|json|csv",
  "include_annotations": true,
  "language_filter": "en|pidgin|all"
}
```

**Response**: Links to downloadable dataset files in specified format.

### 4. System Performance Metrics

**Endpoint**: `GET /api/v1/export/system-metrics`

**Description**: Export system performance and reliability data.

**Response Example**:
```json
{
  "performance_metrics": {
    "availability": {
      "uptime_percentage": 99.9,
      "total_downtime_minutes": 43.2
    },
    "response_times": {
      "average_ms": 1245,
      "p95_ms": 2100,
      "p99_ms": 3200
    },
    "accuracy_metrics": {
      "medical_accuracy_rate": 94.2,
      "user_satisfaction": 4.3,
      "professional_approval_rate": 91.8
    }
  }
}
```

---

## 📁 Data Formats and Schemas

### JSON Schema for Conversation Data
```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "object",
  "properties": {
    "conversation_id": {
      "type": "string",
      "pattern": "^anonymous_conv_[0-9]+$"
    },
    "timestamp": {
      "type": "string",
      "format": "date-time"
    },
    "category": {
      "type": "string",
      "enum": ["general", "sti", "contraception", "emergency", "education"]
    },
    "user_demographics": {
      "type": "object",
      "properties": {
        "age_range": {
          "type": "string",
          "enum": ["15-20", "20-25", "25-30", "30-35", "35-40", "40-45", "45-49"]
        },
        "region": {
          "type": "string"
        }
      }
    }
  },
  "required": ["conversation_id", "timestamp", "category"]
}
```

### CSV Format Example
```csv
conversation_id,timestamp,category,age_range,region,total_messages,satisfaction_rating
anonymous_conv_001,2025-01-15T14:22:00Z,sti_information,20-25,west_africa,8,4
anonymous_conv_002,2025-01-15T15:30:00Z,contraception,25-30,east_africa,6,5
```

### FHIR-Compatible Format
```json
{
  "resourceType": "DiagnosticReport",
  "id": "megasai-interaction-001",
  "status": "final",
  "category": [
    {
      "coding": [
        {
          "system": "http://terminology.hl7.org/CodeSystem/v2-0074",
          "code": "LAB",
          "display": "Health Information"
        }
      ]
    }
  ],
  "subject": {
    "reference": "Patient/anonymous-001"
  },
  "conclusion": "Sexual health information provided"
}
```

---

## 🔒 Privacy and Security Measures

### Data Anonymization
- **User Identifiers**: All replaced with anonymous IDs
- **Temporal Fuzzing**: Timestamps rounded to nearest hour
- **Geographic Generalization**: Precise locations generalized to regions
- **Content Sanitization**: Personal details removed from conversation content

### Access Controls
- **Role-Based Access**: Different data sets for different user types
- **Rate Limiting**: Maximum 1000 requests per hour per API key
- **Audit Logging**: All data access requests logged and monitored
- **Consent Verification**: Only data from consenting users included

### Compliance Standards
- **GDPR Article 20**: Right to data portability
- **HIPAA Safe Harbor**: De-identification standards
- **ISO 27001**: Information security management
- **OpenAPI 3.0**: Standardized API documentation

---

## 💻 Code Examples

### Python Data Extraction
```python
import requests
import pandas as pd
from datetime import datetime, timedelta

class MegasaiDataExtractor:
    def __init__(self, api_key):
        self.api_key = api_key
        self.base_url = "https://api.megasai.org/v1"
        self.headers = {
            "Authorization": f"Bearer {api_key}",
            "Content-Type": "application/json"
        }
    
    def export_conversations(self, date_from, date_to, format="json"):
        """Export conversation data for analysis."""
        params = {
            "date_from": date_from,
            "date_to": date_to,
            "format": format,
            "include_metadata": True
        }
        
        response = requests.get(
            f"{self.base_url}/export/conversations",
            headers=self.headers,
            params=params
        )
        
        if response.status_code == 200:
            if format == "json":
                return response.json()
            elif format == "csv":
                return pd.read_csv(response.content)
        else:
            raise Exception(f"API Error: {response.status_code}")
    
    def get_health_statistics(self, aggregation="monthly"):
        """Get aggregated health statistics."""
        params = {"aggregation_level": aggregation}
        
        response = requests.get(
            f"{self.base_url}/export/health-statistics",
            headers=self.headers,
            params=params
        )
        
        return response.json()

# Usage example
extractor = MegasaiDataExtractor("your_api_key_here")

# Export last month's conversations
last_month = datetime.now() - timedelta(days=30)
conversations = extractor.export_conversations(
    date_from=last_month.strftime("%Y-%m-%d"),
    date_to=datetime.now().strftime("%Y-%m-%d")
)

# Get health statistics
stats = extractor.get_health_statistics()
print(f"Total queries this month: {stats['statistics']['queries_by_category']}")
```

### R Data Analysis
```r
library(httr)
library(jsonlite)
library(dplyr)

# MEGASAI Data Extraction Function
extract_megasai_data <- function(api_key, endpoint, params = list()) {
  base_url <- "https://api.megasai.org/v1"
  
  response <- GET(
    url = paste0(base_url, "/export/", endpoint),
    add_headers(Authorization = paste("Bearer", api_key)),
    query = params
  )
  
  if (status_code(response) == 200) {
    return(content(response, "parsed"))
  } else {
    stop(paste("API Error:", status_code(response)))
  }
}

# Extract and analyze conversation data
conversations <- extract_megasai_data(
  api_key = "your_api_key",
  endpoint = "conversations",
  params = list(
    date_from = "2025-01-01",
    date_to = "2025-01-17",
    format = "json"
  )
)

# Convert to data frame for analysis
conv_df <- conversations$conversations %>%
  map_dfr(~ data.frame(
    category = .x$category,
    satisfaction = .x$interaction_data$satisfaction_rating,
    duration = .x$interaction_data$session_duration_minutes
  ))

# Basic analysis
summary_stats <- conv_df %>%
  group_by(category) %>%
  summarise(
    avg_satisfaction = mean(satisfaction, na.rm = TRUE),
    avg_duration = mean(duration, na.rm = TRUE),
    total_conversations = n()
  )

print(summary_stats)
```

### JavaScript/Node.js Integration
```javascript
const axios = require('axios');

class MegasaiAPI {
  constructor(apiKey) {
    this.apiKey = apiKey;
    this.baseURL = 'https://api.megasai.org/v1';
    this.headers = {
      'Authorization': `Bearer ${apiKey}`,
      'Content-Type': 'application/json'
    };
  }

  async exportData(endpoint, params = {}) {
    try {
      const response = await axios.get(
        `${this.baseURL}/export/${endpoint}`,
        { 
          headers: this.headers,
          params: params 
        }
      );
      return response.data;
    } catch (error) {
      throw new Error(`API Error: ${error.response?.status} - ${error.message}`);
    }
  }

  async getConversations(dateFrom, dateTo) {
    return await this.exportData('conversations', {
      date_from: dateFrom,
      date_to: dateTo,
      format: 'json',
      include_metadata: true
    });
  }

  async getHealthStats() {
    return await this.exportData('health-statistics', {
      aggregation_level: 'monthly'
    });
  }
}

// Usage
const megasai = new MegasaiAPI('your_api_key');

megasai.getConversations('2025-01-01', '2025-01-17')
  .then(data => {
    console.log(`Exported ${data.metadata.total_records} conversations`);
    // Process data as needed
  })
  .catch(error => console.error('Error:', error.message));
```

---

## 📊 Data Export Automation

### Automated Export Script
```bash
#!/bin/bash
# automated-export.sh - Schedule regular data exports

API_KEY="your_api_key"
BASE_URL="https://api.megasai.org/v1"
OUTPUT_DIR="/data/megasai-exports"

# Create timestamped directory
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
EXPORT_DIR="$OUTPUT_DIR/export_$TIMESTAMP"
mkdir -p "$EXPORT_DIR"

# Export conversations (last 7 days)
DATE_FROM=$(date -d '7 days ago' '+%Y-%m-%d')
DATE_TO=$(date '+%Y-%m-%d')

echo "Exporting conversations from $DATE_FROM to $DATE_TO..."
curl -H "Authorization: Bearer $API_KEY" \
     -G "$BASE_URL/export/conversations" \
     -d "date_from=$DATE_FROM" \
     -d "date_to=$DATE_TO" \
     -d "format=json" \
     -o "$EXPORT_DIR/conversations.json"

# Export health statistics
echo "Exporting health statistics..."
curl -H "Authorization: Bearer $API_KEY" \
     -G "$BASE_URL/export/health-statistics" \
     -d "aggregation_level=weekly" \
     -o "$EXPORT_DIR/health_statistics.json"

# Create data package
echo "Creating data package..."
cd "$OUTPUT_DIR"
tar -czf "megasai_export_$TIMESTAMP.tar.gz" "export_$TIMESTAMP/"

echo "Export completed: $OUTPUT_DIR/megasai_export_$TIMESTAMP.tar.gz"
```

---

## 🛡️ Rate Limits and Fair Use

### API Rate Limits
| User Type | Requests/Hour | Daily Limit | Burst Limit |
|-----------|---------------|-------------|-------------|
| **Research** | 1,000 | 10,000 | 50/minute |
| **Healthcare** | 2,000 | 20,000 | 100/minute |
| **Public Health** | 5,000 | 50,000 | 200/minute |
| **Development** | 500 | 5,000 | 25/minute |

### Fair Use Guidelines
- **Research Purposes**: Academic and non-commercial research encouraged
- **Commercial Use**: Contact `teammegas62@gmail.com` for commercial licensing
- **Bulk Exports**: Large data requests require prior approval
- **Caching**: Implement reasonable caching to minimize API calls

---

## 🔧 Implementation Guide

### Setting Up Data Pipeline
1. **Obtain API Key**: Contact appropriate team based on use case
2. **Test Connection**: Use provided code examples to verify access
3. **Design Export Schedule**: Plan regular exports based on needs
4. **Implement Processing**: Set up data processing pipeline
5. **Monitor Usage**: Track API usage against limits
6. **Backup Strategy**: Implement local data backup procedures

### Best Practices
- **Incremental Exports**: Export data in date ranges to avoid large transfers
- **Error Handling**: Implement robust error handling and retry logic
- **Data Validation**: Validate exported data integrity
- **Privacy Compliance**: Ensure your use complies with local privacy laws
- **Attribution**: Consider citing MEGASAI when publishing derived research

---

## 📞 Support and Contact

### Technical Support
- **API Issues**: `teammegas62@gmail.com`
- **Data Questions**: `teammegas62@gmail.com`
- **Integration Help**: `teammegas62@gmail.com`
- **Research Collaboration**: `teammegas62@gmail.com`

### Documentation Updates
- **Version History**: Available in GitHub repository
- **Change Notifications**: Subscribe to API updates mailing list
- **Feedback**: Contribute improvements via GitHub issues

### Emergency Contact
- **System Outages**: `+233555225870`
- **Security Issues**: `teammegas62@gmail.com`
- **Data Breaches**: `teammegas62@gmail.com`

---

## 📚 Additional Resources

### Related Documentation
- [MEGASAI API Reference](docs/API-REFERENCE.md)
- [Data Privacy Policy](docs/PRIVACY-POLICY.md)
- [Terms of Service](docs/TERMS-OF-SERVICE.md)
- [Dataset Card](docs/DATASET-CARD.md)

### External Standards
- [FHIR R4 Specification](https://hl7.org/fhir/R4/)
- [OpenAPI 3.0 Specification](https://swagger.io/specification/)
- [JSON Schema Specification](https://json-schema.org/)
- [GDPR Data Portability Guidelines](https://ec.europa.eu/info/law/law-topic/data-protection_en)

### Community Resources
- **GitHub Repository**: [https://github.com/oMarquess/megasai](https://github.com/oMarquess/megasai)
- **Developer Community**: [https://community.megasai.org](https://community.megasai.org)
- **API Status Page**: [https://status.megasai.org](https://status.megasai.org)

---

**Last Updated**: January 17, 2025  
**Document Version**: 1.0  
**Next Review**: April 17, 2025

---

*This API documentation is part of MEGASAI's commitment to open data and transparency. We encourage responsible use of this data to advance global sexual health outcomes.* 