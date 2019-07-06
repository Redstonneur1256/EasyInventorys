Hi, if you are here its maybe because you want to know how to use multipages system.

Example plugin with one Wool block putting on page 2 and a log block to go back on page 1
With a stone block saying hello form page <CurrentPage>

So, you need to create you class extending Gui

```
public class MyGui extends Gui
```

After that is done, you need a constructor
```
	public MyGui(Player player) {
		super(player, // The player to open Menu
    		"Hello",  // Menu title
        6,        // Menu lines
        2         // Max pages
        );
	}
```

Well, now need to override update method for make this gui

```
	@Override
	public void update(Player arg0) {
		setPage(1, new GuiPage(this) { // Init the page "1" with a new Page (you can create it into a new classe extending GuiPage :)
			public void onPageLoad() { // Method called when player go on the wanted page
				clear(); // Clearing other items from older pages
				setSlotData("Next page", Material.WOOL, 0, new String[0], "page_next"); // "page_next" action is directly into plugin and don't do anything into ths next/previous page is upped to pages amount or under 0
				setSlotData("Hello", Material.STONE, 1, new String[0], "hello"); // Basic item creation with action "hello"
			}
			@Override
			public void onClick(Player player, ItemStack stack, String action) {
				if(action.equals("hello"))
					player.sendMessage("§aHello from page 1"); // When player click, say to it is on page one
			}
		});
		setPage(2, new GuiPage(this) { // Init the page "2" with a new Page (you can create it into a new classe extending GuiPage :)
			public void onPageLoad() { // Method called when player go on this page
				clear(); // Clearing other items from older pages
				setSlotData("Prev page", Material.LOG, 0, new String[0], "page_previous"); // "page_previous" action is directly into plugin and don't do anything into ths next/
				setSlotData("hello", Material.STONE, 1, new String[0], "hello"); // Basic item creation with action "hello"
				
			}
			@Override
			public void onClick(Player player, ItemStack stack, String action) {
				if(action.equals("hello"))
					player.sendMessage("§aHello from page 2"); // When player click on page, say to it is on page two
			}
		});
	}
```

Tada! 🎉Your page system is working.
