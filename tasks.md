1. [ ] Remove many subsections and flatten the document; maybe you could aim for 3–4 major sections per chapter instead and use subsubsections more sparingly, this simply stretches your document horizontally without creating structure and content. The overall appearance should resemble a book or a research paper.
2. [ ] Reorganize experiments by research questions (RQs) with explicit subsections mapping to each RQ, rather than scattering results across format–codec combinations.
3. [ ] Remove scientifically irrelevant configuration listings from the main text.
4. [ ] Tighten prose: many sentences repeat information or contain some obvious points.
5. [ ] Eliminate vague statements like "seems to be limited to" in favor of precise claims backed by quantitative evidence.
6. [ ] Focus on the scientific aspects; move most listings, bucket id, technical details, notebook environment descriptions, and "real" code snippets to the appendix; keep in mind that your code is part of the degree project, not just the document.
7. [ ] Consider removing compute node specifications, Amazon product IDs, and S3 bucket names from the main text; these are technical details, not scientific contributions.

8. [ ] Decrease plot label font sizes using (e.g., `set_size_inches`) appropriately; tiny labels make e.g., figures 5.2, 5.4 and others rather unreadable.
9. [ ] Consider merging figures 5.4 and 5.5 by grouping box plots with respect to file formats.
10. [ ] Maybe include a comparison plot of gzip vs zstd to help the reader to understand the suitable codec for your data.
11. [ ] Move many figures and tables to the appendix; the main body is overloaded with data that is not contextualize and discussed.
12. [ ] Add context to every table and plot in the main body of the text, then refer to the tables: state why each result exists, what `patterns' do we see, and what is the take-away presented by data.
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
