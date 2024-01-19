# amazonsearch

package testintroduction;

import java.util.Base64;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class Amazonsearch {

	public static void main(String[] args) throws Exception  {
		// Launch the Chrome browser
        WebDriver driver = new ChromeDriver();

        // Navigate to the e-commerce website-amazon
        driver.get("https://www.amazon.in/ap/signin?openid.pape.max_auth_age=0&openid.return_to=https%3A%2F%2Fwww.amazon.in%2F%3F%26tag%3Dgooghydrabk1-21%26ref%3Dnav_custrec_signin%26adgrpid%3D155259813593%26hvpone%3D%26hvptwo%3D%26hvadid%3D676742245387%26hvpos%3D%26hvnetw%3Dg%26hvrand%3D14802391232399155249%26hvqmt%3De%26hvdev%3Dc%26hvdvcmdl%3D%26hvlocint%3D%26hvlocphy%3D9075342%26hvtargid%3Dkwd-64107830%26hydadcr%3D14452_2367551&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.assoc_handle=inflex&openid.mode=checkid_setup&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0");
        driver.manage().window().maximize();

        // Wait for a few seconds to ensure the page is fully loaded
        Thread.sleep(2000);
     
        // Login logic
        // Enter username
        

        WebElement usernameTxt = driver.findElement(By.name("email"));
        usernameTxt.sendKeys("kavyasreekavya14@gmail.com");
        driver.findElement(By.className("a-button-input")).click();
        
        //Enter password
        
        WebElement passwordInput = driver.findElement(By.name("password"));
        String decryptedpassword = returnDecryptedpassword("S0thdnlhQDEyMw==");
        passwordInput.sendKeys(decryptedpassword);
        driver.findElement(By.className("a-button-input")).click();


        // Wait for a few seconds to ensure the login is complete
        Thread.sleep(2000);


        // Search for ear pods on the product list page
        WebElement searchbar = driver.findElement(By.xpath("//input[@id=\"twotabsearchtextbox\"]"));
        searchbar.sendKeys("ear pods");
        driver.findElement(By.xpath("//input[@id=\"nav-search-submit-button\"]")).click();
        
        // Wait for a few seconds to let the search results load
        Thread.sleep(5000);
        

        // Select the 3rd item in the search results and add it to the cart
        WebElement thirdItem = driver.findElement(By.xpath("//button[@id='a-autoid-3-announce']"));
        thirdItem.click();
        
        
        // Wait for a few seconds to let the item be added to the cart
        Thread.sleep(5000);

        // Close the browser
        driver.quit();


	}

	public static String returnDecryptedpassword(String encryptedpassword)
	{
		byte[]decryptedpasswordInbytes= Base64.getDecoder().decode(encryptedpassword);
		String decryptedpasswordInText = new String(decryptedpasswordInbytes);
		return decryptedpasswordInText;
	}
}
