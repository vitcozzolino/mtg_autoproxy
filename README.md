<img src="img/mtg_autoproxy.jpg" alt="Generated with https://openart.ai/" width="120" height="120">

# MTG Autoproxy

MTG Autoproxy is a Python program to automatically generate a vendor-specific list of MTG proxies. Currently, the only supported vendor is Blacklotus [1](https://www.aliexpress.com/item/1005001356681692.html?spm=a2g0o.store_home.productList_1386204970.subject_0), [2](https://docs.google.com/spreadsheets/d/1E2iSRhhNUjaZ3MblXx_rflpOIkMwK40OgX5X6yXE4zw/edit#gid=1033599937).

For example, if you have `Ancient Tomb` in the list of wanted cards, the program will select the matching proxy card for it (in this case, `Ancient Tomb English`) based on [Jaro–Winkler distance](http://en.wikipedia.org/wiki/Jaro%E2%80%93Winkler_distance). In the case of blacklotus, it also prioritises regular cards (non foil/holo).

MTG Autoproxy supports loading of a `csv` file from disk (check the `res` folder) or Google Spreadsheets from a remote link.

As `output`, it generates a `csv` with the list of [card name, set, quantity] matching with the cards offered by the specific vendor. Additionally, it will generate a `missing.txt` file with the cards that were not found.

Finally, MTG Autoproxy is not fail proof! Always double check the output before ordering your proxies :)

# Prerequisites

- Python 3.x or higher
- A list of wanted cards formatted as `res/example.csv`
  
# Running MTG Autoproxy

1. Install the required libraries with `pip install -r requirements.txt`
2. Open `config.py` and edit the following variables:
   1. `URI`: should be set to the url of the Google Spreadsheets to download. If you provide a path, it will instead load a csv file from disk.
   2. `EXIT_AT_FIRST_MATCH`: If set to False, the program will  add to the output list **all** matches found for each card (useful when you want to manually select a specific version/art).
3. Run `python main.py`.
4. Check the output in `output/order.csv` and `order/missing.txt`.

# Planned Improvements

- Add more customization options (e.g., preferred card art, preferred card language, etc.).
- Improve search loop.
- Adjust cost calculation based on vendor's discount table.
- Support multiple vendors.
- Simplify `csv` structure and automate retrieval of vendors's list (have the user write only the wanted cards and quantity).

