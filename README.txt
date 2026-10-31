PR evidence: isolated row_has_bold coordinate fix

Read PR_DESCRIPTION.txt for scope, attribution, results, and build limitations.
proposed.patch targets upstream main d2423b1367bcc9721ea7e994e710e5bc7ea91b09.
The eight added tests generate their PDFs in memory; no fixture download is needed for them.
With a correctly built PyMuPDF from the patched checkout, run from the repository root:
  PYMUPDF_SYSINSTALL_ROOT=- PYMUPDF_TEST_USE_LAYOUT=0 PYMUPDF_TEST_USE_4LLM=0 python -m pytest tests/test_tables.py -k test_table_header_bold_uses_page_coordinates

Recorded main-source runs reused released 2.0 binary components (MuPDF 1.28.5).
They are not a full main build or a full repository-suite result.
Only four log files have been path-sanitized; their assertions/results are unchanged.
Earlier failed setup attempts tried loading main table.py without the other main Python modules,
and failed on a missing _layout_available API. Those setup logs are retained locally.
The recorded validation instead used the complete main Python layer, not an API stub.

release_2_0_evidence.zip is the earlier independent released-version experiment.
Its report correctly describes the state at that earlier time; the present archive adds
main-source table-suite and isolated 180-page native-detection comparisons.
The nested archive includes reproduce.py, ten focused unittest cases, and before/after JSON.
Synthetic PDF page 1 remains an open-table failure, unrelated to this patch; page 2 demonstrates
the closed-grid header bug. synthetic_header_preview.png renders page 2.
No manufacturer PDF pages, screenshots, or extracted text are included.
Document summaries disclose changed page numbers, not redistributed source material.
