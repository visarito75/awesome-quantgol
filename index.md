{% capture lista %}{% include_relative README.md %}{% endcapture %}{{ lista | remove_first: "# awesome-quantgol" }}
