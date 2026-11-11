# UiPath PDF Book Splitter & Rebuilder

An automated UiPath workflow (.NET 6 / Modern Experience) that splits dual-page PDF book scans into single pages, re-numbers them in order, and exports a new PDF.

## What it does

- **Screen capture**: Takes screenshots of dual-page spreads directly inside Adobe Acrobat.
- **Auto-cropping**: Crops each spread into separate left and right page images (`590px` width clipping).
- **Natural sorting**: Uses LINQ Regex to keep files ordered properly (`page_1.png` through `page_10.png` instead of standard alphabetical sort).
- **PDF rebuild**: Merges the cropped PNGs into a clean single-page PDF via `UiPath.PDF.Activities`.

## Requirements

- **UiPath Studio** (v2023.x / v2024.x or newer)
- **Activities**:
  - `UiPath.UIAutomation.Activities`
  - `UiPath.PDF.Activities`
  - `UiPath.System.Activities`
- **Adobe Acrobat Reader / Pro DC**

## Arguments

| Argument | Type | Direction | Default | Description |
|---|---|---|---|---|
| `in_PdfFilePath` | `String` | In | *Optional* | Path to the source PDF |
| `in_OutputFolder` | `String` | In | `C:\Users\...\Downloads\ss\` | Output path for temporary PNGs and final PDF |
| `in_OutputPdfName` | `String` | In | `book.pdf` | Target PDF file name |
| `in_TotalSheets` | `Int32` | In | `143` | Number of dual-page spreads to process |
| `in_StartSheet` | `Int32` | In | `3` | Initial sheet number in Acrobat |

## How to run

1. Open your document in **Adobe Acrobat**.
2. Open `Main.xaml` in UiPath Studio.
3. Update `in_OutputFolder` and `in_TotalSheets` in the Arguments panel.
4. Run `Main.xaml` (`Ctrl + F6`).
