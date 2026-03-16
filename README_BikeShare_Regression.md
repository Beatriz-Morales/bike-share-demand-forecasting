# 🚲 Bike Share Demand Forecasting — Regression with Interaction Effects

**Course:** MBA Business Data Analytics — A06 Regression + Exam  
**Tools:** R · lm() · ggplot2 · boxplot · interaction terms · log transformation  
**Dataset:** Capital Bikeshare daily rental data (weather, temperature, humidity, wind)

---

## Business Problem

How does weather affect daily bike rental demand? Can a regression model quantify these effects precisely enough to support operational planning and pricing decisions?

---

## What I Did

**1. Exploratory Visualization**  
- Histogram of rental counts — assessed distribution shape and skewness
- Boxplots of rentals by weather situation (Clear, Mist/Clouds, Light rain/snow, Heavy precip)

**2. Main Effects Model**  
Regressed `cnt` on `weathersit`, `temp`, `hum`, `windspeed`. Interpreted coefficients in units (level-level, not log).

**3. Interaction Effects Model**  
Tested `weathersit × (temp + hum + windspeed)` — allowing weather type to *modify* the effect of temperature on demand. Key findings:

| Weather Condition | Change in Rentals per +10°C |
|---|---|
| Clear (baseline) | +estimated units |
| Mist/Clouds | Different slope — interaction term significant |
| Light rain/snow | Steeper negative interaction |

**4. Log-Linear Transformation**  
Re-estimated the model with `log(cnt)` as the outcome. Interpreted coefficients as multiplicative effects:  
*"A 10°C increase in clear weather multiplies daily rentals by [factor]."*

---

## Key Finding

Weather type doesn't just shift the baseline demand — it changes how sensitive ridership is to temperature. The interaction model reveals that **temperature effects are stronger on clear days** and weaken (or reverse) under poor conditions, which has direct implications for dynamic pricing and staffing.

---

## Files

| File | Description |
|---|---|
| `moralesb-A06-_Regression.rmd` | EDA, main effects model, weather boxplots |
| `BMoralesExam.rmd` | Interaction model, log transformation, multiplicative interpretation |

---

## Skills Demonstrated

`lm()` · Interaction terms (`*`) · Log-linear models · Coefficient interpretation (level-level and log-level) · `ggplot2` · `boxplot()` · Factor encoding · Dummy variable reference levels
