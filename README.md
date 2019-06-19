# BMO_CODE_TEST
BMO_CODE_TEST
package intro_2_restart;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.ClickAction;

public class BMO_TEST_CODE_RUN {

	public static void main(String[] args) throws InterruptedException {
		// TODO Auto-generated method stub

		// setting up the chrome drivers path
       System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
       
       
		// we are creating an instance of the WebDriver interface and casting it to chromeDriver Class.
       // WebDriver is an interface, driver is a reference variable, chromeDriver() is a Constructor, new is a keyword, and new chromeDriver() is an Object.
		WebDriver driver = new ChromeDriver();
		
		//invoking the given URL 'https://www.just-eat.co.uk/'
		driver.get("https://www.just-eat.co.uk/");
		
		//validating the title of URL to check whether we are opening right page or not
		System.out.println("title of the URL page" + driver.getTitle());
		
		// we can also validate page opening by this method also
		//System.out.println(driver.getCurrentUrl());
		
	
		// finding the search box and sending postal code 'AR51 1AA'
		driver.findElement(By.xpath("//*[@id=\"skipToMain\"]/form/div/div/label/input")).sendKeys("AR51 1AA" + Keys.ENTER);
		
		
		// finding the total number of links or list of restaurants available in the page
		// every link in a page is uniquely identified with a tagname called anchor tag 'a'
		// all restaurants in the given area are divided into three categories  1.open restaurants 2.closed restaurants 3. offline restaurants 
		// we finding the particular divisions of all types of resturants and finding the anchor tags within that division to identify total number of restaurants 
		
		//all restaurants regardless of their availability 
		WebElement all_restaurants = driver.findElement(By.xpath("//*[@id=\"skipToMain\"]/main/div/div[2]/div[2]"));
		int linkcount_all_restaurants = all_restaurants.findElements(By.tagName("a")).size();
		System.out.println("Total number of Restaurants in your area AR51 1AA : "+ linkcount_all_restaurants);
		
		//open resturants
		WebElement open_restaurants = driver.findElement(By.xpath("//*[@id=\"skipToMain\"]/main/div/div[2]/div[2]/div[1]/div"));
		int linkcount_open_restaurants = open_restaurants.findElements(By.tagName("a")).size();
		System.out.println("total number of available resturants open currently : "+ linkcount_open_restaurants);
		
		//closed restaurants
		WebElement closed_restaurants = driver.findElement(By.xpath("//*[@id=\"skipToMain\"]/main/div/div[2]/div[2]/div[2]/div"));
		int linkcount_closed_restaurants = closed_restaurants.findElements(By.tagName("a")).size();
		System.out.println("total number of currently closed restaurants : "+ linkcount_closed_restaurants);
		
		//offline restaurants		
		WebElement offline_restaurants = driver.findElement(By.xpath("//*[@id=\"skipToMain\"]/main/div/div[2]/div[2]/div[3]/div"));
		int linkcount_offline_restaurants = offline_restaurants.findElements(By.tagName("a")).size();
		System.out.println("total number of offline restaurants currently : "+linkcount_offline_restaurants);
		// validating the number of resturants and links correctly whether they are matching with total count and individual  counts
		int restaurants = linkcount_open_restaurants + linkcount_closed_restaurants + linkcount_offline_restaurants;
		System.out.println("total count of restaurants"+restaurants);
		
		//ordering food from restaurant
		// selecting restaurant and opening it
		driver.findElement(By.xpath(".//a[@href='/restaurants-reorder-test-case-restaurant-51/menu']")).click();
		
		// verifying opened page title with our desired restaurant 
		System.out.println(driver.getTitle());
			
		
		
		//driver.findElement(By.xpath("//*[@id=\"cat0\"]/div/div[2]/div[2]/div/form/div/button")).click();
		
	    //	driver.findElement(By.xpath("//*[contains(text(),'Chicken & Bacon')]/parent::div/div[@class='orderDetail']/descendant::button[@class='addButton ']")).click();
		
		// finding required item locator and adding to the cart
		
		//adding chicken to cart
		WebElement chicken_bacon = driver.findElement(By.xpath("//*[@id=\"cat0\"]/div/div[2]/div[2]"));
		
		((JavascriptExecutor) driver).executeScript("arguments[0].scrollIntoView(true);", chicken_bacon);
		Thread.sleep(500);
		
	    chicken_bacon.findElement(By.xpath("//*[@id=\"cat0\"]/div/div[2]/div[2]/div/form/div/button")).click();
	    System.out.println("chciken and bacon added to cart");
	    
	    // adding pizza to the cart
	    WebElement massive_pizza = driver.findElement(By.xpath("//*[@id=\"cat1\"]/div/div[1]"));
		
		((JavascriptExecutor) driver).executeScript("arguments[0].scrollIntoView(true);", massive_pizza);
		Thread.sleep(500);
		
	    massive_pizza.findElement(By.xpath("//*[@id=\"cat1\"]/div/div[1]/div[2]/div/form/div/button")).click();
	    
		System.out.println("pizza added to cart");
		
		// we are not checking out because of captcha .
		//driver.findElement(By.xpath("//*[@id=\"menuCheckout\"]/button")).click();
		
		// google captcha is obstructing the for executing the check out
		
		// google captcha is also obstructing the login page
		
		// if google captcha was disabled a lot of other actions can be done while writing this code.
		
		
		
	driver.close();
		
		
		
		
		
		
	}

}
