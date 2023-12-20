# unit and time fixed effects

fatality.fte <- plm(mrall ~ beertax, data = fatality.pd,
model = "within", effect="twoways")
summary(fatality.fte, vcov = vcovHC)

# clustered std error
m1coeffs_cl <- coeftest(m1, vcov = vcovCL, cluster = ~idcode)
