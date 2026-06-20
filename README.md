<!--
  README de profil. Remplace USERNAME par ton pseudo GitHub dans les liens
  ci-dessous, puis place ce fichier dans un repo public portant ce même pseudo.
-->

## Compétences / Skills

- Langages : Python, C++, C#, TypeScript, SQL, VBA
- Quant & data : NumPy, pandas, scikit-learn, Gurobi, Streamlit
- Outils : Git, Linux, React Native / Expo, Supabase
- Domaines : pricing d'options, calcul stochastique, risque de marché (VaR, ES, EVT), risque de contrepartie, arbitrage statistique

## Projets / Projects

### Finance quantitative

**Arbitrage statistique — marché du blé**
Stratégie market-neutral exploitant les relations de cointégration entre le future sur le blé et un panier d'actions agricoles : signaux Z-score et optimisation quadratique sous contraintes via Gurobi. Sharpe de 1,14 et Calmar de 1,46 sur la version pairs trading.
A market-neutral strategy built on cointegration between the wheat futures contract and a basket of agricultural equities, using Z-score signals and constrained quadratic optimization with Gurobi. Sharpe of 1.14 and Calmar of 1.46 on the pairs-trading variant.
Technologies : Python, Gurobi, statsmodels
[Repository](https://github.com/USERNAME/wheat-stat-arb)

**Market Risk — VaR, Expected Shortfall et théorie des valeurs extrêmes**
Mesures de risque sur l'action Natixis, implémentées sans aucune librairie : VaR historique non-paramétrique (noyau biweight), backtesting hors-échantillon, Expected Shortfall, estimation de la queue de distribution par l'estimateur de Pickands et modèle d'impact prix de Bouchaud.
Risk measures on the Natixis stock, implemented from scratch with no libraries: non-parametric historical VaR (biweight kernel), out-of-sample backtesting, Expected Shortfall, tail estimation via the Pickands estimator, and the Bouchaud price-impact model.
Technologies : Python, Excel
[Repository](https://github.com/USERNAME/market-risk-var-evt)

**Bibliothèque de pricing d'options en C++**
Valorisation d'options européennes, digitales, américaines et asiatiques via trois moteurs : formule fermée de Black-Scholes (avec le delta), arbre binomial de Cox-Ross-Rubinstein gérant l'exercice anticipé, et simulation Monte-Carlo avec intervalle de confiance. Architecture orientée objet par héritage.
Pricing of European, digital, American and Asian options through three engines: the Black-Scholes closed-form solution (with delta), a Cox-Ross-Rubinstein binomial tree handling early exercise, and Monte-Carlo simulation with a confidence interval. Object-oriented design based on inheritance.
Technologies : C++
[Repository](https://github.com/USERNAME/cpp-option-pricer)

### Machine learning

**Machine Learning for Asset Management**
Comparaison entre régression linéaire (OLS) et arbres de régression pour prédire le spot EUR/USD à partir d'indicateurs techniques (MACD, RSI), puis construction de portefeuille par Hierarchical Risk Parity.
Comparison of linear regression (OLS) and regression trees to forecast the EUR/USD spot from technical indicators (MACD, RSI), followed by portfolio construction using Hierarchical Risk Parity.
Technologies : Python, scikit-learn
[Repository](https://github.com/USERNAME/ml-asset-management)

### Logiciel et données

**Analyse des avis et alertes ANSSI**
Pipeline Python collectant les flux RSS de l'ANSSI, identifiant les CVE, les enrichissant via les API MITRE (CVSS, CWE) et EPSS, consolidant le tout dans un DataFrame pandas, puis produisant visualisations et alertes email.
A Python pipeline that collects ANSSI RSS feeds, identifies CVEs, enriches them through the MITRE (CVSS, CWE) and EPSS APIs, consolidates everything into a pandas DataFrame, and produces visualizations and email alerts.
Technologies : Python, pandas
[Repository](https://github.com/USERNAME/anssi-cve-analysis)

### Application

**my-movie**
Application de notation de films et séries (React Native / Expo, Supabase) : recherche filtrée par genre et décennie, suggestions par swipe, disponibilité par plateforme de streaming en France, et profil avec statistiques et badges.
A movie and TV rating app (React Native / Expo, Supabase): genre- and decade-filtered search, swipe-based suggestions, French streaming availability, and a profile with statistics and badges.
Technologies : React Native, Expo, TypeScript, Supabase
[Repository](https://github.com/USERNAME/my-movie)
