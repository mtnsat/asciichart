# asciichart

> A port of the npm package [asciichart](https://github.com/kroitor/asciichart) by Igor [Kroitor](https://github.com/kroitor).

Just used to plot ascii line charts, no dependencies.

![asciichart](images/asciichart.png)

## Usage

This is a header only library, you can copy all files in [include](./include) directory to your project.

## Options

The width of the chart equals to the length of data series. The height and range will be determined automatically. Users can specify:

1. height: height of chart.
2. offset: axis offset from the left (min 2).
3. colors: colors used in chart.
4. min: min value.
5. max: max value.
6. symbols: symbols used in chart.

## Examples

### Scale to Desired height

```c++
std::vector<double> series; // range from -15 to +15
for (int i = 0; i < 200; i += 2)
{
series.push_back(15 * std::cos(i * (kPI * 8) / 120));
}

Asciichart asciichart(std::vector<std::vector<double>>{series});
std::wcout << '\n'
           << asciichart.height(10).Plot() // rescale to -3 ~ +3 lines
           << '\n';
```

![scale](images/asciichart.png)

### Multiple Series

```c++
std::vector<double> series;
for (int i = 0; i < 200; i += 2)
{
series.push_back(15 * std::cos(i * (kPI * 8) / 120));
}

std::vector<double> series2;
for (int i = 0; i < 200; i += 2)
{
series2.push_back(15 * std::sin(i * ((kPI * 4) / 100)));
}
Asciichart asciichart(std::vector<std::vector<double>>{series, series2});
std::wcout  << '\n'
            << asciichart.height(6).Plot() 
            << '\n';
```

![multiple](images/multiple.png)