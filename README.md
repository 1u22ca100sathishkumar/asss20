# asss20
1. Mouse hover to "Tutorials" and click "Dot Net" submenu

URL: https://www.hyrtutorials.com/

Selenium Java Program
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;

public class MouseHoverExample {

    public static void main(String[] args) {

        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        driver.get("https://www.hyrtutorials.com/");

        // Locate "Tutorials" menu
        WebElement tutorialsMenu = driver.findElement(By.xpath("//a[text()='Tutorials']"));

        // Mouse hover
        Actions actions = new Actions(driver);
        actions.moveToElement(tutorialsMenu).perform();

        // Click "Dot Net" submenu
        WebElement dotNetSubMenu = driver.findElement(By.xpath("//a[text()='Dot Net']"));
        dotNetSubMenu.click();

        System.out.println("Navigated to Dot Net tutorial page");

        driver.quit();
    }
}

✅ Explanation

Actions class → Used for mouse hover

moveToElement() → Performs hover

Submenu is clicked after hover

2. Copy "locked_out_user" and password and paste into login form

URL: https://www.saucedemo.com/

Selenium Java Program
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import java.awt.Toolkit;
import java.awt.datatransfer.StringSelection;
import java.awt.datatransfer.Clipboard;

public class CopyPasteLogin {

    public static void main(String[] args) throws InterruptedException {

        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        driver.get("https://www.saucedemo.com/");

        // Copy username to clipboard
        String usernameText = "locked_out_user";
        StringSelection usernameSelection = new StringSelection(usernameText);
        Clipboard clipboard = Toolkit.getDefaultToolkit().getSystemClipboard();
        clipboard.setContents(usernameSelection, null);

        // Paste username in Username field
        WebElement usernameField = driver.findElement(By.id("user-name"));
        usernameField.sendKeys(usernameText);

        // Copy password to clipboard
        String passwordText = "secret_sauce";
        StringSelection passwordSelection = new StringSelection(passwordText);
        clipboard.setContents(passwordSelection, null);

        // Paste password in Password field
        WebElement passwordField = driver.findElement(By.id("password"));
        passwordField.sendKeys(passwordText);

        // Click Login
        driver.findElement(By.id("login-button")).click();

        System.out.println("Login attempted with copied credentials");

        driver.quit();
    }
}
