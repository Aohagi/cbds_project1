n <- power.t.test(power = 0.9, delta = .01, sd = .04, type = "one.sample", alt = "one.sided")$n
n
ceiling(n/10)*10