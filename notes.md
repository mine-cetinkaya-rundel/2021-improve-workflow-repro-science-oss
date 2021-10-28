## demo: rmarkdown

- Insert image from a URL:
	- https://allisonhorst.github.io/palmerpenguins/reference/figures/culmen_depth.png
	- Penguin bill dimensions

- Insert citation
	- https://doi.org/10.1371/journal.pone.0090081
	- The data come from @gorman2014
	- Add # References section at bottom

- Add inline code
	- The original dataset has 3 species (Adelie, Gentoo, and Chinstrap), but we will only work with Adelie and Chinstrap species.

	becomes

	- The original dataset has `r penguins$species %>% unique() %>% length()` species (`r glue_collapse(penguins$species %>% unique(), sep = ", ", last = ", and ")`), but we will only work with `r glue_collapse(penguins_nongentoo$species %>% unique(), sep = " and ")` species.

- Insert figure referencing

output: 
  bookdown::html_document2:
    fig_caption: yes

- Multiple figures in one

fig.asp = 0.8, out.width = "100%", 


p1 <- ggplot(penguins, aes(x = bill_length_mm, y = bill_depth_mm, color = species)) +
  geom_point()

p2 <- ggplot(penguins, aes(x = flipper_length_mm, y = body_mass_g, color = species)) +
  geom_point()

p3 <- ggplot(penguins, aes(x = body_mass_g, fill = species)) +
  geom_histogram(alpha = 0.5) +
  guides(fill = FALSE)

(p1 + p2) / p3 +
  plot_annotation(
    tag_levels = "A",
    title = "The surprising truth about penguins",
    subtitle = "These 3 plots will reveal yet-untold secrets about our beloved data-set",
    caption = "Disclaimer: None of these plots are insightful"
    ) + 
  plot_layout(guides = "collect") & theme(legend.position = "bottom")

- Turn off all code

## demo: github

.gitignore add keynote and notes.md

