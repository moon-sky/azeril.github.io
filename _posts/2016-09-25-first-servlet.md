---
layout: post
titile: Servlet初识
decription: 此一次接触servlet，好多东西都不太清楚，也作为入门的一篇吧
categories: Blog
---



## First Servlet(Servlet 学习日记)

### 前期准备

1. IDE: MyEclipse 2014
### 详细步骤

1. 新建一个web project
2. 右键新建servlet![](http://i.imgur.com/plxDtCd.png)
3.代码详细如下

		import java.io.DataOutputStream;
		import java.io.IOException;
		import java.io.PrintWriter;
		
		import javax.servlet.ServletException;
		import javax.servlet.http.HttpServlet;
		import javax.servlet.http.HttpServletRequest;
		import javax.servlet.http.HttpServletResponse;
		
		import net.sf.json.JSONObject;
		
		public class Test extends HttpServlet {

		/**
		 * Constructor of the object.
		 */
		public Test() {
			super();
		}
	
		/**
		 * Destruction of the servlet. <br>
		 */
		public void destroy() {
			super.destroy(); // Just puts "destroy" string in log
			// Put your code here
		}
	
		/**
		 * The doGet method of the servlet. <br>
		 *
		 * This method is called when a form has its tag value method equals to get.
		 * 
		 * @param request the request send by the client to the server
		 * @param response the response send by the server to the client
		 * @throws ServletException if an error occurred
		 * @throws IOException if an error occurred
		 */
		public void doGet(HttpServletRequest request, HttpServletResponse response)
				throws ServletException, IOException {
			String username=request.getParameter("username");
			String password=request.getParameter("password");
			DataOutputStream outputStream=new DataOutputStream(response.getOutputStream());
			outputStream.writeChars("success");
			
			JSONObject obj=new JSONObject();
			obj.put("username", "moon-sky");
			obj.put("password", "hello");
			outputStream.writeChars(obj.toString());
			outputStream.close();
			
			/*response.setContentType("text/html");
			PrintWriter out = response.getWriter();
			
			out.println("<!DOCTYPE HTML PUBLIC \"-//W3C//DTD HTML 4.01 Transitional//EN\">");
			out.println("<HTML>");
			out.println("  <HEAD><TITLE>A Servlet</TITLE></HEAD>");
			out.println("  <BODY>");
			out.print("    This is ");
			out.print(this.getClass());
			out.println(", using the GET method");
			out.println("  </BODY>");
			out.println("</HTML>");
			out.flush();
			out.close();*/
		}
	
		/**
		 * The doPost method of the servlet. <br>
		 *
		 * This method is called when a form has its tag value method equals to post.
		 * 
		 * @param request the request send by the client to the server
		 * @param response the response send by the server to the client
		 * @throws ServletException if an error occurred
		 * @throws IOException if an error occurred
		 */
		public void doPost(HttpServletRequest request, HttpServletResponse response)
				throws ServletException, IOException {
	
			response.setContentType("text/html");
			PrintWriter out = response.getWriter();
			out.println("<!DOCTYPE HTML PUBLIC \"-//W3C//DTD HTML 4.01 Transitional//EN\">");
			out.println("<HTML>");
			out.println("  <HEAD><TITLE>A Servlet</TITLE></HEAD>");
			out.println("  <BODY>");
			out.print("    This is ");
			out.print(this.getClass());
			out.println(", using the POST method");
			out.println("  </BODY>");
			out.println("</HTML>");
			out.flush();
			out.close();
		}
	
		/**
		 * Initialization of the servlet. <br>
		 *
		 * @throws ServletException if an error occurs
		 */
		public void init() throws ServletException {
			// Put your code here
		}
	
		}`
1. 其中涉及到使用json包，这里还需要到一些挫折，刚开始的时候是按照Android 中的习惯，把json-lib-2.3-jdk15.jar直接添加进来，但是发现还是在运行过程中，报错**java.lang.ClassNotFoundException: org.apache.commons.collections.map.ListOrderedMap**，最终解决方法是直接把把jar包放到WEB-INF 的lib目录![](http://i.imgur.com/PoIpZ34.png)
2. 最后一步，右键运行
![](http://i.imgur.com/Ek7ZtYG.png)
1. 然后在浏览器输入：![](http://i.imgur.com/VD82hrs.png)