# unit and time fixed effects

fatality.fte <- plm(mrall ~ beertax, data = fatality.pd,
model = "within", effect="twoways")
summary(fatality.fte, vcov = vcovHC)

# clustered std error
m1coeffs_cl <- coeftest(m1, vcov = vcovCL, cluster = ~idcode)

# two steps for iv reg

library(AER)
tsls <- ivreg(log(packpc) ~ log(realprice) | salestax, data = data1)
coeftest(tsls, vcov = vcovHC, type = "HC1")

# pooling regression
fatality.pool <- plm(mrall~beertax, data = fatality.pd, model = "pooling")

summary(fatality.pool, vcov = vcovHC)
