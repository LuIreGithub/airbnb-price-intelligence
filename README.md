# Marseille Airbnb Price Analysis

Machine learning project exploring the factors associated with Airbnb nightly prices in Marseille, France.

The project combines property characteristics, geographic information and amenities data to evaluate how accurately nightly prices can be estimated using machine learning.

## Project Overview

The objective of this project is not to build a production-ready Airbnb pricing system, but to investigate how much pricing information can be captured from publicly available listing characteristics.

The analysis follows an end-to-end machine learning workflow:

- Data exploration and cleaning
- Outlier analysis
- Feature selection and engineering
- Linear Regression baseline
- Random Forest Regression
- Cross-validation
- Hyperparameter tuning with GridSearchCV
- Geographic clustering with K-Means
- Integration of a separate amenities dataset
- Feature importance analysis
- Error analysis
- Log-target experiment

## Data

The project uses Airbnb listing and amenities data for Marseille, France.

The main dataset contains property characteristics, geographic information and nightly prices.

A second amenities dataset was aggregated at listing level using `Airbnb_ListingID`. From this dataset, several features were engineered, including:

- Total amenity count
- Air conditioning
- Parking
- Outdoor space
- Beach access
- Sea view
- Pool availability

Amenities information was available for 3,918 of the 5,758 listings in the modeling sample.

## Modeling

Linear Regression was first used as a baseline.

A Random Forest model was then introduced to capture non-linear relationships between property characteristics and nightly price. Cross-validation and GridSearchCV were used to control overfitting and tune model complexity.

Additional feature-engineering experiments included property type extraction and geographic clustering.

The largest improvement came from integrating amenities information.

### Final Model Performance

| Metric | Result |
|---|---:|
| Test R² | 0.657 |
| Test MAE | €46.45 |
| Test RMSE | €82.68 |
| 5-fold CV R² | 0.624 ± 0.046 |

The enriched model was evaluated on the subset of listings for which amenities information was available.

## Key Findings

Property size and capacity were the strongest predictors of nightly price.

The most influential features included:

1. Bedrooms
2. Bathrooms
3. Beds
4. Guest capacity
5. Pool availability
6. Latitude
7. Total amenity count
8. Longitude

Adding amenities improved test R² from approximately 0.621 to 0.657 when evaluated on the same listings and train/test split.

## Error Analysis

Model performance varied substantially across price segments.

The model performed considerably better for lower- and mid-priced listings than for premium properties. High-priced listings were frequently underestimated, suggesting that the available data does not fully capture characteristics associated with luxury properties.

A logarithmic target transformation improved prediction errors for listings below €200 per night but worsened performance for premium listings.

## Limitations

Several limitations should be considered:

- Amenities information was unavailable for part of the dataset.
- Premium listings were relatively rare.
- Important qualitative characteristics such as interior quality, luxury level, exact views and property condition were unavailable.
- The model should therefore not be interpreted as a production-ready pricing tool.

## Technologies

- Python
- pandas
- NumPy
- scikit-learn
- Matplotlib
- Jupyter

## Repository

The complete analysis, from data exploration to model evaluation and error analysis, is available in:

`airbnb_marseille_analysis.ipynb`

---

### 🇫🇷 Résumé

Ce projet de Data Science analyse les facteurs associés aux prix des logements Airbnb à Marseille et évalue différentes approches de Machine Learning pour l'estimation du prix par nuit.

Le projet comprend le nettoyage et l'exploration des données, le feature engineering, la validation croisée, l'optimisation d'un Random Forest, l'intégration de données supplémentaires sur les équipements et une analyse détaillée des erreurs.

La documentation technique et le notebook sont rédigés en anglais.