# jdbc_to_mysqlconnection
package com.bce.JDBC;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.sql.PreparedStatement;

public class Mysql_Connection {

	public static void main(String[] args)throws SQLException ,ClassNotFoundException {
		//create basic variable 
				Connection con=null;
				ResultSet rs=null;
				Statement st=null;
				try {
				Class.forName("com.mysql.jdbc.Driver");
				//establish the connection 
				con=DriverManager.getConnection("jdbc:mysql://localhost:3306/student","root","saka");
                //create statement object
				if(con!=null)
	             st=con.createStatement();
				//execuate sql queary 
				if(st!=null)
				rs=st.executeQuery("select * from students");
				//print data record 
				if(rs!=null) {
					while(rs.next()) {
						
						System.out.println(rs.getString(1)+" "+rs.getString(2)+" "+rs.getInt(3));
					}//end of the while block
				}//end of the if block
				}catch(SQLException e) {
					e.printStackTrace();
				}//end of the catch block 
				catch(ClassNotFoundException e) {
					e.printStackTrace();
				}//end of the catch block 
				catch(Exception e) {
					e.printStackTrace();
				}//end of the catch block 
				finally {
					try {
						if(rs!=null)
							rs.close();
					}catch(SQLException e) {
						e.printStackTrace();
					}//end of teh catch block
					try {
						if(st!=null)
							st.close();
					}catch(SQLException e) {
						e.printStackTrace();
					}//end 
					try {
						if(con!=null)
							con.close();
					}catch(SQLException e) {
						e.printStackTrace();
					}//end of the catch block
					
				}//end of the finally block
	}//end of the main method 

}//class
