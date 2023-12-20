# unit and time fixed effects

fatality.fte <- plm(mrall ~ beertax, data = fatality.pd,
model = "within", effect="twoways")
summary(fatality.fte, vcov = vcovHC)

# clustered std error
