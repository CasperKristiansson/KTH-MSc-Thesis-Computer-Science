1. [x] Remove many subsections and flatten the document; maybe you could aim for 3–4 major sections per chapter instead and use subsubsections more sparingly, this simply stretches your document horizontally without creating structure and content. The overall appearance should resemble a book or a research paper.

- Q: I reduced the major sections tag and restructured the document. When I did this it initially resulted in more sections and using more \paragraph{} tags. I did put some effort into merging sections. But I'm wondering is the current state acceptable? Or should I simply try to merging more sections into each other?
- Changes: https://github.com/CasperKristiansson/KTH-MSc-Thesis-Computer-Science/compare/277f075ff5c595dff8c2feef963c67b578aeea37...f2d4c375e7af513ccb859a13b94ce27ad22fa561

2. [x] Reorganize experiments by research questions (RQs) with explicit subsections mapping to each RQ, rather than scattering results across format–codec combinations.

- Changes: https://github.com/CasperKristiansson/KTH-MSc-Thesis-Computer-Science/commit/2b33953a82759b13ba85385201a097c6e7529978

3. [x] Remove scientifically irrelevant configuration listings from the main text.

- Changes: https://github.com/CasperKristiansson/KTH-MSc-Thesis-Computer-Science/compare/2b33953a82759b13ba85385201a097c6e7529978...ec2f4ffb380f8ef6bfd981a1223b952b4cbcbc17

4. [x] Tighten prose: many sentences repeat information or contain some obvious points.
5. [x] Eliminate vague statements like "seems to be limited to" in favor of precise claims backed by quantitative evidence.
6. [x] Focus on the scientific aspects; move most listings, bucket id, technical details, notebook environment descriptions, and "real" code snippets to the appendix; keep in mind that your code is part of the degree project, not just the document.
7. [x] Consider removing compute node specifications, Amazon product IDs, and S3 bucket names from the main text; these are technical details, not scientific contributions.

- Changes for 4-7: https://github.com/CasperKristiansson/KTH-MSc-Thesis-Computer-Science/compare/ec2f4ffb380f8ef6bfd981a1223b952b4cbcbc17...1c632dece8fd9d26269f33a619555dbbc37d0b52

8. [x] Decrease plot label font sizes using (e.g., `set_size_inches`) appropriately; tiny labels make e.g., figures 5.2, 5.4 and others rather unreadable.

- I did this;
  mpl.rcParams.update({
  "font.size": 8, # base font
  "axes.labelsize": 8,
  "axes.titlesize": 9,
  "xtick.labelsize": 7,
  "ytick.labelsize": 7,
  "legend.fontsize": 7,
  })

TEXTWIDTH_IN = 5.8 (figures width)

Some graphs was also broken down into multiple plots to make them more readable. Also tried to improve with using tight_layout() and adjusting figure sizes. But as you mentioned, I sat the set_size_inches to match the text width.

- Q: Is this acceptable? Or should I optimize it more for each figure?

9. [x] Consider merging figures 5.4 and 5.5 by grouping box plots with respect to file formats.
10. [x] Maybe include a comparison plot of gzip vs zstd to help the reader to understand the suitable codec for your data.
11. [x] Move many figures and tables to the appendix; the main body is overloaded with data that is not contextualize and discussed.
12. [x] Add context to every table and plot in the main body of the text, then refer to the tables: state why each result exists, what `patterns' do we see, and what is the take-away presented by data.

- Changes for 10-12: https://github.com/CasperKristiansson/KTH-MSc-Thesis-Computer-Science/commit/0e7487780902e430127e1d41a0ac020782691aef

13. [ ] Clarify that your "consistency" claims are regarding the average scores of some experiments; figures 5.11 and 5.12 show the variance demonstrates a somewhat unreliable mean estimate for TileDB and Zarr in certain conditions.
14. [ ] Describe file formats more precisely as a computer scientist; explain what each format does beyond naming conventions, and what the strength and weaknesses are, and how this leads to research questions and experiments.
15. [ ] Consider include experiments with slicing in dimensions other than the default; multi-axis access is common in real workflows (if needed), and consider discussing the relationship between storage order (C vs Fortran) in HDF5 and slicing performance.
16. [ ] Consider testing EBS volumes for HDF5, as they are reported to be faster by a significant margin compared to HSDS.
17. [ ] HSDS is a managed infrastructure and you partially measure HSDS infrastructure/"spin-up" time; can you isolate this from the file format performance? I suspect that your experiments are likely far too small to demonstrate when HSDS is useful.
18. [ ] Explicitly state which hypotheses each experiment tests and link results back to those hypotheses.
19. [ ] Consider reporting effect sizes (not just p-values) for all comparisons; confidence intervals alone are insufficient.
20. [ ] Do you compute FWER / FDR?
21. [ ] Clarify the scope: your session-conditional, descriptive contrasts do your results actually support a causal claim in general? I suspect that your experimental setup is not strong enough for this.
22. [ ] Specify, motivate, and formally introduce statistical hypothesis, and explain how the test works, why you have chosen it over alternatives, provide context.
