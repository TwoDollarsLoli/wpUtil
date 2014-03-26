/**
 * 
 */
package wpUtil;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.io.PrintWriter;
import java.util.ArrayList;
import java.util.List;

/**
 * @author Wp
 * 
 */
public class BoOperateTXT
{

	/**
	 * 将内容一行一行的写入到指定的TXT文件
	 * 
	 * @param path 要写入的文件全路径
	 * @param str 要写入的内容
	 * @param isAppend 是否采用追加方式写入
	 */
	public static void writeTXT(String path, String str, boolean isAppend) throws Exception
	{
		//实例化一个文件
		File file = new File(path);
		//判断文件是否存在，若不存在则创建一个新文件
		if (!file.exists()) file.createNewFile();
		if (!file.exists()) throw new Exception("文件创建失败，无法写入！");//若创建失败则抛出异常
		PrintWriter pw = null;//定义一个输出内容的对象
		try
		{//定义文件的输出流,true表明若多次调用此方法并且path一样，则会将之后的内容以追加的方式写入到上一个文件中否则是覆盖
			FileOutputStream fos = new FileOutputStream(path, isAppend);// true表明会追加内容
			pw = new PrintWriter(fos);//将文件流放入输出内容的对象中
			pw.println(str);//输出内容
			pw.flush();//释放资源
		} catch (FileNotFoundException e)
		{
			e.printStackTrace();
		} finally
		{
			try
			{//关闭输出对象
				pw.close();
			} catch (Exception e)
			{
				e.printStackTrace();
			}
		}
	}
	
	
	/**
	 * 将内容一行一行的写入到指定的TXT文件
	 * 
	 * @param path 要写入的文件全路径
	 * @param str 要写入的内容
	 * @param isAppend 是否采用追加方式写入
	 */
	public static void writeTXT(String path, String str) throws Exception
	{//调用方法写入内容，默认采用追加方式写入
		writeTXT(path, str, true);
	}
	
	/**
	 * 一行行的读取Txt文本内容
	 * 
	 * @param path
	 */
	public static String readTXT(String path) throws Exception
	{
		File file = new File(path);//实例化文件对象
		if (!file.exists()) return null;//如果文件不存在则返回null
		//实例化一个接收内容的对象
		BufferedReader reader = new BufferedReader(new FileReader(file));
		//定义一个字符串变量用于接收内容并返回
		StringBuffer sb = new StringBuffer("");
		while(true)
		{//死循环，当遇到空行是退出
			String value = reader.readLine();//接收每行内容
			if(value==null) break;//判断是否为空，若是则退出
			sb.append(value);//将非空内容添加到字符串中
		}
		reader.close();//关闭接收内容的对象
		return sb.toString();//返回内容的字符串
	}

	/**
	 * 一行行的读取Txt文本内容
	 * 
	 * @param path
	 */
	public static List<String> readTXTReList(String path) throws Exception
	{
		File file = new File(path);//实例化文件对象
		if (!file.exists()) return null;//如果文件不存在则返回null
		//实例化一个接收内容的对象
		BufferedReader reader = new BufferedReader(new FileReader(file));
		//定义一个List集合变量用于接收内容并返回
		List<String> list = new ArrayList<String>();
		while(true)
		{//死循环，当遇到空行是退出
			String value = reader.readLine();//接收每行内容
			if(value==null) break;//判断是否为空，若是则退出
			list.add(value);//将非空内容添加到List集合中
		}
		reader.close();//关闭接收内容的对象
		return list;//返回内容的List集合
	}

	
	/**
	 * 读取指定行数的内容（行号从1开始）
	 * 
	 * @param path
	 * @param num 行号从1开始计算
	 * @param map
	 */
	public static String readTXT(String path,int num) throws Exception
	{
		File file = new File(path);//实例化文件对象
		if (!file.exists()) return null;//如果文件不存在则返回null
		//实例化一个接收内容的对象
		BufferedReader reader = new BufferedReader(new FileReader(file));
		//定义一个字符串用于接收内容并返回
		StringBuffer sb = new StringBuffer("");
		int i = 1;//定义Txt行号
		while(true)
		{//死循环，循环到指定行时读取内容并返回
			if(i != num)
			{//当不是指定行时
				reader.readLine();//空读取内容（做一个读取，但是不接收）注：reader对象必须执行readLine方法才能进入下一行
				i ++ ;//累加行号
				continue;//进入下一个循环
			}
			//当循环到指定行号时，读取内容并保存到字符串中
			String value = reader.readLine();
			sb.append(value);//将内容放到字符串中
			break;//对出读取
		}
		reader.close();//关闭读取对象
		return sb.toString();//返回读到的内容
	}

	/**
	 * 读取指定行数之间的内容（行号从1计算，读取从指定行开始，读取到结束行）
	 * 
	 * @param path
	 * @param num 行号从1开始
	 * @param map
	 */
	public static String[] readTXT(String path, int startNum, int endNum) throws Exception
	{
		String[] txtArr = null;//定义一个空的数组
		File file = new File(path);//实例化文件对象
		if (!file.exists()) return txtArr;//如果文件不存在则返回null
		//实例化一个接收内容的对象
		BufferedReader reader = new BufferedReader(new FileReader(file));
		//实例化一个数组（长度为结束行+1-开始行，此算法算出的长度是包含起始行和结束行的长度）
		txtArr = new String[endNum + 1 - startNum];
		int i = 1;//Txt文本的行号
		int j = 0;//数组的下标
		while(true)
		{//死循环，循环读取指定行之间的内容
			if(i < startNum)
			{//当未到开始行时
				reader.readLine();//空读取内容（做一个读取，但是不接收）注：reader对象必须执行readLine方法才能进入下一行
				i ++ ;//累加行号
				continue;//进入下一个循环
			}
			//当循环到指定行号时，读取内容并保存到字符串中
			String value = reader.readLine();
			txtArr[j] = value;//将内容放到数组中
			if(i == endNum)//当达到结束行时
				break;//退出循环
			i ++;//累加行号
			j ++;//累加数组下标
		}
		reader.close();//关闭读取对象
		return txtArr;//返回数组
	}

	
	public static void main(String[] args)
	{
		try
		{
//			String str = BoOperateTXT.readTXT("D:/2011全年临时文件保存目录/20111029机构撤并/234table.txt",5);
			String[] txtArr = BoOperateTXT.readTXT("C:\\Users\\Wp\\Desktop\\需要修改的意见.txt",9,11);
			for (int i = 0; i < txtArr.length; i++)
			{
				System.out.println("["+i+"]=["+txtArr[i]+"]");
			}
//			List<String> txtList = BoOperateTXT.readTXTReList("C:\\Users\\Wp\\Desktop\\需要修改的意见.txt") ;
//			for (int i = 0; i < txtList.size(); i++)
//			{
//				System.out.println("["+(i+1)+"]=["+txtList.get(i)+"]");
//			}
//			System.out.println(str);
//			BoOperateTXT.writeTXT("d:/tddownload/xieheyikedaxue.txt",
//					"aaaaaaaaaaaaaaaaaa\n");
//			BoOperateTXT.writeTXT("d:/tddownload/xieheyikedaxue.txt",
//					"bbbbbbbbbbbbbbbb");
		} catch (Exception e)
		{
			e.printStackTrace();
		}
	}
}
