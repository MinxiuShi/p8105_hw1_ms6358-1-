# p8105_hw1_ms6358-1-
The chunk below creates a dataframe containing a sample of size 10 from a random normal variable, constructs the specified logical vector indicating whether elements of the sample are greater than 0, character vector of length 10 and factor vectorof length 10, with 3 different factor “levels”.The code chunk also finds the mean of the sample and stores it for easy in-line printing.

```{r}
library(tidyverse)

example_df = tibble(
  vec_numeric = rnorm(10,sd = 1),
  vec_logical = vec_numeric > 0,
  vec_char = c("This", "is", "my", "first", "homework", "for", "the", "course", "Data", "Science"),
  vec_factor = factor(c("good", "good", "good", "great", "great", "great", "excellent", "excellent", "excellent", "excellent"))
)

#I'm gonna take this function to calculate the mean
mean_vec_numeric = mean(pull(example_df, vec_numeric))

mean_vec_logical = mean(pull(example_df, vec_logical))
 
mean_vec_char = mean(pull(example_df, vec_char))

mean_vec_factor = mean(pull(example_df, vec_factor))

We fail to get the mean of character vector and factor vector since they are neithor numbers or logicals, character and factor can't calculate mean.
```

```{r}
install.packages("palmerpenguins")

data("penguins", package = "palmerpenguins")

The dataset contains a sample of size 344, constructs the specified species island,bill_length_mm, bill_depth_mm, flipper_length_mm, body_mass_g, sex. The number of rows of the dataset is `r nrow(penguins)` and the numbers of columns of the datasetsis `r ncol(penguins)`.The mean of the flipper length is `r mean(pull(penguins, flipper_length_mm))`.

#draw the scatterplot
p1 = ggplot(penguins, aes(x = bill_length_mm, y = flipper_length_mm, color = species)) + geom_point()

ggsave("plot.png", p1)
```

