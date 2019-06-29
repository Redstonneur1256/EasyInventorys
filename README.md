# EasyInventorys

EasyInventorys is an API to create menu easily

Example menu:

```
import org.bukkit.Material;
import org.bukkit.entity.Player;
import org.bukkit.inventory.ItemStack;
import org.bukkit.inventory.meta.ItemMeta;

import fr.redstonneur1256.easyinv.Gui;

public class ExampleGui extends Gui {

	public ExampleGui() {
		/*
		 * Setting name "MyCoolGui" and amount of line to 3 
		 * Warning! Amount of line need to be between 1 and 6
		 */
		super("MyCoolGui", 3);
	}
	
	@Override
	public void update(Player player) {
		/* 
		 * Creating a wool block named "MyCoolBlock"
		 * With lore "Click to say hello"
		*/
		ItemStack myCoolItem = new ItemStack(Material.WOOL);
		ItemMeta myCoolItemMeta = myCoolItem.getItemMeta();
		myCoolItemMeta.setDisplayName("MyCoolBlock");
		myCoolItem.setItemMeta(myCoolItemMeta);
		
		/*
		 * Setting my wool into slot "0" with action "say_Hello"
		 */
		setSlotData(myCoolItem, 0, "say_Hello");
	}
	
	@Override
	public void onClick(Player player, ItemStack stack, String action) {
		if(action == "say_Hello")
			player.performCommand("say Hello");
	}
	
}
```
