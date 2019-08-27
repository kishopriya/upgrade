# upgrade
Code cahllenge
package selenium;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;

public class Upgradeflow {

	WebDriver driver;

	public void invokebrowser() {
		System.setProperty("webdriver.chrome.driver",
				"D:\\selenium-java-2.53.1\\chromedriver_win32\\chromedriver.exe");
		driver = new ChromeDriver();
		driver.manage().deleteAllCookies();
		driver.manage().window().maximize();
		driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
		driver.manage().timeouts().pageLoadTimeout(30, TimeUnit.SECONDS);
		checkyourrate();
		basicinformation();
		captureinformation();
		// validateinformation();
		// driver.close();
	}

	public void checkyourrate() {
		driver.get("https://www.credify.tech/phone/nonDMFunnel");
		driver.findElement(By.xpath("//input[@name='desiredAmount']"))
				.sendKeys("5000");
		driver.findElement(By.xpath("//select[@class='sc-fAjcbJ bvkLRg']"))
				.click();
		driver.findElement(By.xpath("//option[@value='HOME_IMPROVEMENT']"))
				.click();
		driver.findElement(By.xpath("//select[@class='sc-fAjcbJ bvkLRg']"))
				.click();
		// WebElement DropLoanPurpose =
		// driver.findElement(By.className("sc-fAjcbJ bvkLRg"));
		// Select select = new Select(DropLoanPurpose);
		// select.selectByVisibleText("HOME_IMPROVEMENT");
		driver.findElement(By.xpath("//button[@type='submit']")).click();

	}

	public void basicinformation() {
		driver.findElement(By.xpath("//div[contains(text(),'Individual')]"))
				.isEnabled();
		driver.findElement(By.xpath("//input[@name='borrowerFirstName']"))
				.sendKeys("kishlaks");
		driver.findElement(By.xpath("//input[@name='borrowerLastName']"))
				.sendKeys("ram");
		driver.findElement(By.xpath("//input[@name='borrowerStreet']"))
				.sendKeys("25 Henry Smith Ave");
		driver.findElement(By.xpath("//input[@name='borrowerCity']")).sendKeys(
				"Stafford");
		driver.findElement(By.xpath("//input[@name='borrowerState']"))
				.sendKeys("VA");
		driver.findElement(By.xpath("//input[@name='borrowerDateOfBirth']"))
				.sendKeys("02/12/1980");
		driver.findElement(By.xpath("//input[@name='borrowerZipCode']"))
				.sendKeys("22554");
		driver.findElement(By.xpath("//input[@name='borrowerIncome']"))
				.sendKeys("$45000");
		driver.findElement(
				By.xpath("//input[@name='borrowerAdditionalIncome']"))
				.sendKeys("$55000");
		driver.findElement(By.xpath("//input[@name='username']")).sendKeys(
				"kishpra@gmail.com");
		driver.findElement(By.xpath("//input[@name='password']")).sendKeys(
				"Ultimate123!");
		driver.findElement(
				By.xpath("//div[@class='sc-kfGgVZ sc-esjQYD fCisXT']")).click();
		driver.findElement(By.xpath("//button[@type='submit']")).click();

		// WebElement Element1 =
		// driver.findElement(By.xpath("//span[@class='sc-chPdSV VlhWk']"));
		// System.out.println("Your Loan amount is:"+Element1);

	}

	public void captureinformation() {

		WebElement ActYourLoanAmount = driver.findElement(By
				.xpath("//div[contains(text(),'Your Loan Amount')]"));
		System.out.println(ActYourLoanAmount.getText());
		WebElement ActLoanAmount = driver.findElement(By
				.xpath("//span[@class='sc-chPdSV VlhWk']"));
		System.out.println(ActLoanAmount.getText());
		WebElement ActMonthlyPayment = driver.findElement(By
				.xpath("//span[@data-auto='defaultMonthlyPayment']"));
		System.out.println("MonthlyPayment is" + ActMonthlyPayment.getText());
		WebElement ActTermInAPR = driver.findElement(By
				.xpath("//div[@class='section--sm']"));
		System.out.println(ActTermInAPR.getText());
		// Thread.sleep(20);
		try {
			driver.findElement(
					By.xpath("//body/div[@id='root']/div[@class='layout__wrap']/main[@class='container-fluid layout__main layout-default']/div/header[@class='header header--collapsed']/div[@class='header-nav']/label[1]"))
					.click();
			// driver.findElement(By.xpath("//nav[@class='header-nav-menu']//label[@class='header-nav__toggle'][contains(text(),'Menu')]")).click();
			// Thread.sleep(20);
			driver.findElement(By.xpath("//a[contains(text(),'Sign Out')]"))
					.click();
			driver.findElement(By.xpath("//a[contains(text(),'Sign Out')]"))
					.click();
			driver.quit();
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		driver.get("https://www.credify.tech/portal/login");
		driver.findElement(By.xpath("//input[@name='username']")).sendKeys(
				"kishpra@gmail.com");
		driver.findElement(By.xpath("//input[@name='password']")).sendKeys(
				"Ultimate123!");
		// driver.findElement(
		// By.xpath("//div[@class='sc-kfGgVZ sc-esjQYD fCisXT']")).click();
		driver.findElement(By.xpath("//button[@type='submit']")).click();
		WebElement ExpYourLoanAmount = driver.findElement(By
				.xpath("//div[contains(text(),'Your Loan Amount')]"));
		System.out.println(ExpYourLoanAmount.getText());
		WebElement ExpLoanAmount = driver.findElement(By
				.xpath("//span[@class='sc-chPdSV VlhWk']"));
		System.out.println(ExpLoanAmount.getText());
		WebElement ExpMonthlyPayment = driver.findElement(By
				.xpath("//span[@data-auto='defaultMonthlyPayment']"));
		System.out.println("MonthlyPayment is" + ExpMonthlyPayment.getText());
		WebElement ExpTermInAPR = driver.findElement(By
				.xpath("//div[@class='section--sm']"));
		System.out.println(ExpTermInAPR.getText());

		// Assert.assertEquals(ActYourLoanAmount,ExpYourLoanAmount);
		// System.out.println("loan amount match");
		// Assert.assertEquals(ActMonthlyPayment,ExpMonthlyPayment);
		// System.out.println("Monthly payement match");

		if (ExpLoanAmount.equals(ActLoanAmount)) {
			System.out.println("loan amount match");
		} else {
			System.out.println("loan amount mismatch");
		}
		if (ExpMonthlyPayment.equals(ActMonthlyPayment)) {
			System.out.println("payment match");
		} else {
			System.out.println("Payment mismatch");
		}
		if (ActTermInAPR.equals(ExpTermInAPR)) {
			System.out.println("Term match");
		} else {
			System.out.println("Term mismatch");
		}
	}

	// public void signout(){
	// driver.findElement(By.xpath("//body/div[@id='root']/div[@class='layout__wrap']/main[@class='container-fluid layout__main layout-default']/div/header[@class='header header--collapsed']/div[@class='header-nav']/label[1]")).click();
	// driver.findElement(By.xpath("//nav[@class='header-nav-menu']//label[@class='header-nav__toggle'][contains(text(),'Menu')]")).click();
	// driver.findElement(By.xpath("//a[contains(text(),'Sign Out')]")).click();
	// }

	// public void validateinformation(){

	// driver.get("https://www.credify.tech/portal/login");
	// driver.findElement(By.xpath("//input[@name='username']")).sendKeys(
	// "kishpra@gmail.com");
	// driver.findElement(By.xpath("//input[@name='password']")).sendKeys(
	// "Ultimate123!");
	// driver.findElement(
	// By.xpath("//div[@class='sc-kfGgVZ sc-esjQYD fCisXT']")).click();
	// driver.findElement(By.xpath("//button[@type='submit']")).click();

	// }

	public static void main(String[] args) {
		Upgradeflow myOBJ = new Upgradeflow();
		myOBJ.invokebrowser();

	}

}

