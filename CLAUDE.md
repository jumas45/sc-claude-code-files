# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a Claude Code course materials repository containing educational resources and practical examples for learning Claude Code best practices. The main content is organized around three key examples:

- **RAG chatbot codebase** (referenced in links)
- **E-commerce data analysis** (Lesson 7 - primary working code)  
- **Figma design mockup implementation** (referenced materials)

## Primary Working Directory: `sc-claude-code-files/lesson7_files/`

This contains a complete, functional e-commerce business analytics solution with both Jupyter notebook analysis and a Streamlit dashboard.

## Common Development Tasks

### Python Environment Setup
```bash
pip install -r sc-claude-code-files/lesson7_files/requirements.txt
```

### Running the Streamlit Dashboard
```bash
cd sc-claude-code-files/lesson7_files
streamlit run dashboard.py
```

### Running Jupyter Analysis
```bash
cd sc-claude-code-files/lesson7_files
jupyter notebook EDA_Refactored.ipynb
```

## Architecture Overview

### Core Components

1. **Data Loading Module** (`data_loader.py`)
   - `EcommerceDataLoader` class for CSV data ingestion
   - Data cleaning and transformation utilities
   - Configurable filtering (year, month, order status)
   - Creates unified sales datasets from multiple CSV sources

2. **Business Metrics Module** (`business_metrics.py`)
   - `BusinessMetricsCalculator` for KPI calculations
   - `MetricsVisualizer` for chart generation
   - Comprehensive reporting with revenue, satisfaction, delivery metrics
   - Year-over-year comparison capabilities

3. **Dashboard Application** (`dashboard.py`)
   - Professional Streamlit interface
   - Real-time filtering by year/month
   - Interactive Plotly visualizations
   - KPI cards with trend indicators

### Data Pipeline Flow

```
CSV Files → EcommerceDataLoader → Processed DataFrames → BusinessMetricsCalculator → Reports/Visualizations
```

### Key Data Sources

The system expects these CSV files in `ecommerce_data/` directory:
- `orders_dataset.csv` - Order information and timestamps
- `order_items_dataset.csv` - Individual items and pricing
- `products_dataset.csv` - Product categories
- `customers_dataset.csv` - Customer location data
- `order_reviews_dataset.csv` - Customer satisfaction scores
- `order_payments_dataset.csv` - Payment information

## Configuration Patterns

### Analysis Configuration
The notebook uses configurable parameters at the top:
```python
ANALYSIS_YEAR = 2023
COMPARISON_YEAR = 2022  
ANALYSIS_MONTH = None  # or 1-12 for specific month
DATA_PATH = 'ecommerce_data/'
```

### Modular Design
- All business logic is extracted from the notebook into reusable modules
- Data loading is centralized in `EcommerceDataLoader`
- Metrics calculations are handled by `BusinessMetricsCalculator`
- Visualizations are managed by `MetricsVisualizer`

## Development Guidelines

### Working with Data
- Always use `create_sales_dataset()` with appropriate filters
- Default to 'delivered' orders for revenue analysis
- Handle missing data gracefully (modules include error checking)

### Adding New Metrics
1. Extend `BusinessMetricsCalculator` class
2. Add visualization methods to `MetricsVisualizer`
3. Update dashboard to display new metrics

### File Organization
- Keep data processing in `data_loader.py`
- Business logic goes in `business_metrics.py`  
- UI/dashboard code stays in `dashboard.py`
- Analysis workflows belong in Jupyter notebooks

## Notes

- This is primarily a learning/course repository, not a production system
- The main functional code is in the lesson7_files directory
- Other directories contain course notes and reference materials
- No testing framework or CI/CD is configured
- Dependencies are Python data science stack: pandas, plotly, streamlit, jupyter
- The username for git commits should be "jumas45" and the email address is "jumas45@gmail.com"