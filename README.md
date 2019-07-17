package day25;

import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.InputStreamReader;
import java.net.MalformedURLException;
import java.net.URL;
import java.net.URLConnection;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class RegexDemo04 {

	public static void main(String[] args) {
		// TODO 自动生成的方法存根

	}
	//网页爬虫
	public static void getMails_1() throws Exception
	{
		URL url=new URL("http://192.168.1.254:8080/myweb/mail.html");
		URLConnection conn=url.openConnection()
		BufferedReader bufin =new BufferedReader (new InputStreamReader (conn.getInputStream()))	;
		
		String line =null;
		String regex="\\w+@\\w+(\\.\\w+)+";
		
		Pattern p=Pattern.compile(regex);
		while ((line =bufin.readLine())!=null)
		{
			Matcher m=p.matcher(line);
			while (m.find())
			{
				System.out.println(m.group());
			}
		}
	
		
	}
	
public static void getMail () throws Exception
{
	BufferedReader bufr=new BufferedReader (new FileReader ("mail.txt"));
	String line =null;
	String regex="\\w+@\\w+(\\.\\w+)+";
	//调用Pattern 将规则封装 
	Pattern p=Pattern.compile(regex);
	while ((line =bufr.readLine())!=null)
	{
		//让正则表达式和要作用的字符串相关联，让获取匹配器对象
		Matcher m=p.matcher(line);
		while (m.find())
		{
			System.out.println(m.group());
		}
	}
}
}
