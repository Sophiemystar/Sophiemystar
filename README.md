- 👋 Hi, I’m @Sophiemystar
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

Example using Afex for a repeated measures ANOVA followed by graphic.
1---Run the statistical analysis using the afex package
1.	> afmodellabfield <- afex::aov_car(Heartrate ~ Month*Site*Temperature + Error(Mussels/Temperature), data=OctApril_labfieldHRd)
> afmodellabfield
> in this example y is heat rate, month, site and tmperature are fixed factors, the same mussels are measured in the lab and field, the file name is included at the end.
> 
2.**	Then create the Figure:**
p30 <- afex_plot(afmodellabfield, x = "Site", trace = "Temperature", panel= "Month", error = "within",mapping=c("linetype","shape", "fill"), data_geom = ggplot2::geom_violin,data_arg = list(width=0.5), factor_levels = list(Month = c(October = "October 2018", April = "April 2019")))
Renaming/reordering factor levels of 'Month':
  October -> October 2018
April -> April 2019
  p30
3. Then use theme_classic for a nice white background, select the y axis limits and add the y axis labels. In the example below the y axis limits were 30 minimum and 90 maximum value.
p31<-p30+theme_classic(base_size = 20) + ylim(30,90) + labs(y= "Heart rate in beats/minute")
> p31
4. Then move the legend from its current position so that it appears inside the figure. C(0,0) = top left and c(1,1) = top right
p32<-p31+theme(legend.justification = c("right", "top"), legend.position = c(1, 1))

5. Remove the legend title unnecessary and confusing
p32+theme(legend.title = element_blank()) #removes legend.title

Sophiemystar/Sophiemystar is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
