package section1;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import java.time.Duration;

public class AmazonWatchAutomation {
    public static void main(String[] args) {

       
        System.setProperty("webdriver.chrome.driver", "path_to_chromedriver"); 

        
        WebDriver driver = new ChromeDriver();

       
        driver.manage().window().maximize();

        
        driver.get("https://www.amazon.in");

       
        WebElement searchBox = driver.findElement(By.id("twotabsearchtextbox"));
        searchBox.sendKeys("Wrist Watches");
        searchBox.submit();

       
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
        wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//span[contains(text(), 'results')]")));

        
        WebElement leatherFilter = driver.findElement(By.xpath("//li[@aria-label='Leather']//span[@class='a-list-item']"));
        leatherFilter.click();

        
        wait.until(ExpectedConditions.elementToBeClickable(By.xpath("//li[@aria-label='Leather']//span[@class='a-list-item']")));

       
        WebElement fastrackFilter = driver.findElement(By.xpath("//li[@aria-label='Fastrack']//span[@class='a-list-item']"));
        fastrackFilter.click();

       
        wait.until(ExpectedConditions.elementToBeClickable(By.xpath("//li[@aria-label='Fastrack']//span[@class='a-list-item']")));

     
        WebElement nextPageButton = driver.findElement(By.xpath("//a[contains(text(), '2')]"));
        nextPageButton.click();

       
        wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//div[@data-index]")));

       
        WebElement firstProduct = driver.findElement(By.xpath("(//div[@data-index='1']//h2/a)[1]"));
        firstProduct.click();

        
        String originalWindow = driver.getWindowHandle();

        
        for (String handle : driver.getWindowHandles()) {
            if (!handle.equals(originalWindow)) {
                driver.switchTo().window(handle);
                break;
            }
        }

      
        WebElement addToCartButton = wait.until(ExpectedConditions.elementToBeClickable(By.id("add-to-cart-button")));
        addToCartButton.click();

        
        driver.quit();
    }
}


<!---
hemalatha3539/hemalatha3539 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
