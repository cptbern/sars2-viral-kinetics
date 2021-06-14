# Viral kinetics models for SARS-CoV-2 drug repurposing

A collection of R scripts to model the within-host viral kinetics of SARS-CoV-2 and drug effects to inform drug repurposing. You can explore your own drugs by re-running the scripts with simulations or actual experimental data. We supply concentration profiles for several proposed treatments along with [Monolix](https://lixoft.com) / [mlxR](http://simulx.webpopix.org/mlxr) code to repeat our simulations or build your own.

We fitted the viral kinetics to [data published by Young et al.](https://jamanetwork.com/journals/jama/fullarticle/10.1001/jama.2020.3204) in early 2020. Additionally, we allow for acquired immunity to develop over the course of 1-2 weeks based on reports by [Long et al., Nat. Med. 2020](https://www.frontiersin.org/articles/10.3389/fphar.2021.625678/full#B51) and [To et al., Lancet Inf. Dis. 2020](https://www.frontiersin.org/articles/10.3389/fphar.2021.625678/full#B74). For a detailed description, please refer to *"Modeling of SARS-CoV-2 Treatment Effects for Informed Drug Repurposing"* ([Kern et al., Front. Pharmacol. 2021](https://doi.org/10.3389/fphar.2021.625678)).

## Model

The underlying model is the standard target-cell limited model extended with developing acquired immunity and drug effects, both represented by sigmoidal Emax models. Virus particles *V* infect a pool of susceptible (target) cells *T* with the cellular infection rate *β*. Infected cells *I* begin shedding virions at a production rate *p*

$$
\frac{dT}{dt}=-(1-\eta)\beta TV
$$

$$
\frac{dI}{dt}=-(1-\eta)\beta TV - \delta I
$$

$$
\frac{dV}{dt}=(1-\epsilon)pI - cV
$$

where *T* is the time-dependent number of target (susceptible) cells, *I* is the number of infected cells, *V* is the number of circulating virions. The effects of pharmacological treatments by different modes of action are described by the following variables: inhibition of viral entry into susceptible cells, by decreasing the cellular infection rate with effectiveness η, and/or by blocking viral production rate within infected cells with effectiveness ε.
