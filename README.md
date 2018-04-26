# go-metrics-falcon
[falcon-plus](https://github.com/open-falcon/falcon-plus) support for [go-metrics](https://github.com/rcrowley/go-metrics)


## Usage

Create and update metrics:

```

c := metrics.NewCounter()
metrics.Register("foo", c)
c.Inc(47)

g := metrics.NewGauge()
metrics.Register("bar", g)
g.Update(47)

s := metrics.NewExpDecaySample(1028, 0.015) // or metrics.NewUniformSample(1028)
h := metrics.NewHistogram(s)
metrics.Register("baz", h)
h.Update(47)

m := metrics.NewMeter()
metrics.Register("quux", m)
m.Mark(47)

t := metrics.NewTimer()
metrics.Register("bang", t)
t.Time(func() {})
t.Update(47)


```

Periodically report every metric to open falcon.
```
import falconmetrics "github.com/g4zhuj/go-metrics-falcon"

go falconmetrics.ReportRegistry(metrics.DefaultRegistry)
```
