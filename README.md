# 🇳🇵 Nepal Government Office Experience Tracker

Real-time citizen feedback system for Nepal government services with timer-based visit tracking and comprehensive ratings.

## 🌟 Features

### **📍 Complete User Journey**
1. **District Selection**: Choose from all 77 Nepal districts organized by province
2. **Office Selection**: Select office type (DAO, Passport, Transport, etc.) and specific services
3. **🚨 Timer Tracking**: Prominent red button to start visit timing with real-time countdown
4. **Service Completion**: End with "काम भयो" (Success) or "काम भएन" (Failed)
5. **Comprehensive Rating**: 5-star ratings + cultural Nepali feedback questions
6. **Analytics Dashboard**: Office comparisons, rankings, and performance metrics

### **⭐ Rating Categories**
- समग्र अनुभव (Overall Experience)
- कर्मचारीको व्यवहार (Staff Behavior)
- कार्यालयको सफाई (Office Cleanliness)
- प्रक्रियाको दक्षता (Process Efficiency)
- जानकारीको स्पष्टता (Information Clarity)

### **❓ Cultural Feedback Questions**
- घुस माग्यो? (Did they ask for bribe?)
- तपाईंले कतिवटा कोठामा जानुपर्‍यो? (How many rooms did you have to visit?)
- तपाईंले दलाल/एजेन्ट प्रयोग गर्नुपर्‍यो? (Did you have to use agents/brokers?)
- कर्मचारी सहयोगी र विनम्र थिए? (Were staff helpful and polite?)
- प्रक्रिया स्पष्ट र बुझ्न सजिलो थियो? (Was the process clear and easy?)

## 🏢 Office Coverage

### District Administration Offices (10)
- Kathmandu, Lalitpur, Bhaktapur, Chitwan
- Pokhara, Biratnagar, Birgunj, Butwal
- Nepalgunj, Dharan

### Specialized Departments (11)
- Department of Passport
- Department of Transport Management  
- Survey Department
- Department of Land Management
- Land Revenue Offices (3)
- Transport Management Offices (3)
- Company Registrar Office

## 🛠️ Installation

1. **Clone the repository**
```bash
git clone <repository-url>
cd nepal_gov_scraper
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Run the scraper**
```bash
# Full comprehensive scraping (recommended)
python main.py

# Without live data enhancement (faster)
python main.py --no-live-enhancement

# Test office factory only
python main.py --test-only
```

## 📊 Sample Results

The scraper provides comprehensive data including:

### Service Information
- **Citizenship Certificate**: NPR 100-500 (15-20 days / 3-5 days)
- **E-Passport**: NPR 5,000-15,000 (15-30 days / same-day)
- **Driving License**: NPR 1,500 (7-15 days)
- **Vehicle Registration**: NPR 3,000-25,000 (3-7 days)
- **Land Registration**: 2% of property value (15-30 days)

### Coverage Statistics
- **100% Phone Coverage** across all offices
- **88.1% Average Data Completeness**
- **5 Provinces Covered** (Bagmati, Gandaki, Koshi, Lumbini, Madhesh)
- **35 Government Services** documented

## 🧪 Testing

```bash
# Run enhanced DAO Kathmandu test
python test.py

# Test text processing utilities
python tests/test_text_processing.py
```

## 📁 Project Structure

```
nepal_gov_scraper/
├── main.py                 # Main entry point
├── test.py                 # Simple test runner
├── requirements.txt        # Dependencies
├── README.md              # This file
├── COMPREHENSIVE_RESULTS_SUMMARY.md  # Detailed results
├── src/
│   ├── comprehensive_scraper.py      # Main scraper
│   ├── config.py                     # Base configuration
│   ├── config_extended.py           # Extended office data
│   ├── models/
│   │   ├── enhanced_models.py       # Data models
│   │   └── office_factory.py        # Office creation factory
│   └── utils/
│       ├── text_processing.py       # Nepal-specific text processing
│       └── web_utils.py             # Web scraping utilities
├── tests/
│   ├── test_enhanced_dao_kathmandu.py  # Enhanced test scraper
│   └── test_text_processing.py         # Text processing tests
├── data/                    # Output JSON files
├── logs/                    # Log files
└── docs/                    # Additional documentation
```

## 💻 Usage Examples

### Basic Usage
```python
from src.comprehensive_scraper import ComprehensiveNepalGovScraper

scraper = ComprehensiveNepalGovScraper()
output_file = scraper.run_comprehensive_scrape()
print(f"Results saved to: {output_file}")
```

### Query Specific Services
```python
# Get offices offering passport services
passport_offices = scraper.get_offices_by_service('passport')

# Get offices in Bagmati Province  
bagmati_offices = scraper.get_offices_by_province('Bagmati Province')

# Get all DAOs
dao_offices = scraper.get_offices_by_type('district_administration_office')
```

## 📋 Output Format

Results are saved in JSON format with comprehensive metadata:

```json
{
  "metadata": {
    "total_offices": 21,
    "data_quality": "comprehensive_with_live_enhancement",
    "average_completeness": 88.1
  },
  "analysis_report": {
    "overview": { ... },
    "contact_coverage": { ... },
    "geographic_distribution": { ... },
    "service_availability_matrix": { ... }
  },
  "offices": [
    {
      "name": "District Administration Office, Kathmandu",
      "services": [
        {
          "service_name": "Citizenship Certificate", 
          "fees": {
            "normal_processing": {"amount": 100, "processing_days": "15-20 days"},
            "urgent_processing": {"amount": 500, "processing_days": "3-5 days"}
          }
        }
      ],
      "contact": {
        "phone_general": "01-5362828",
        "email": "passport.daoktm@gmail.com"
      },
      "metadata": {
        "completeness_score": 100.0,
        "data_quality": "factory_generated_enhanced_with_live"
      }
    }
  ]
}
```

## 🔧 Configuration

Key configuration files:
- `src/config.py`: Base settings and patterns
- `src/config_extended.py`: Extended office data and service definitions

## 🚀 Production Deployment

The scraper is production-ready with:
- Comprehensive error handling
- Rate limiting and robots.txt compliance
- SSL certificate management
- Detailed logging and monitoring
- Data quality validation

## 📈 Performance

- **21 offices** processed in ~30 seconds
- **88.1% data completeness** on average
- **100% success rate** with error fallbacks
- **Live data enhancement** for 5+ offices

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make changes and test thoroughly
4. Submit a pull request

## 📄 License

This project is for educational and research purposes. Please respect government websites and follow their terms of service.

## 🙏 Acknowledgments

- Nepal Ministry of Home Affairs
- Department of Passport, Nepal
- All government offices providing public service information