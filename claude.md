cat > ~/chicago-crime-dashboard/CLAUDE.md << 'EOF'
# Chicago Crime Dashboard — Claude Code Instructions

## Project
Build a Flexdashboard in R for Urban Crime Pattern Analysis and Hotspot Detection using the Chicago Crime Dataset (2001-2017).

## Goal
Create a single self-contained HTML dashboard file using flexdashboard + plotly + leaflet.

## Data
All data is pre-processed and saved as RDS files in ./data/:
- crime_data_clean.rds — 4.5M rows, cleaned crime data with features
- coords_clusters.rds — 100K sampled coords with K-Means cluster labels
- kmeans_model.rds — trained K-Means model (K=5)
- rf_model.rds — trained Random Forest model

## Tech Stack
- R + flexdashboard
- plotly (interactive charts)
- leaflet (interactive map)
- dplyr, ggplot2, lubridate

## Dashboard Pages
### Page 1: Overview
- Total crimes count (value box)
- Arrest rate % (value box)
- Most common crime type (value box)
- Top 10 crime types bar chart (plotly)
- Crimes by hour line chart (plotly)

### Page 2: Trends
- Crimes by month (plotly)
- Crimes by season (plotly)
- Crimes by year (plotly)
- Heatmap: crime type vs time of day (plotly)

### Page 3: Hotspot Map
- Leaflet map with 5 cluster zones
- Color coded markers by cluster
- Popup showing crime type on click
- Use 10K sample for performance

### Page 4: ML Results
- Random Forest: confusion matrix table
- Random Forest: feature importance bar chart (plotly)
- Linear Regression: note about R2=0.083 and why
- K-Means: cluster size pie chart (plotly)

## Output
- File: chicago_crime_dashboard.Rmd
- Knit to: chicago_crime_dashboard.html

## Instructions for Claude Code
1. Install required packages if not available
2. Write the complete .Rmd file
3. Knit it to HTML using rmarkdown::render()
4. Verify HTML file is created
5. Report done
EOF