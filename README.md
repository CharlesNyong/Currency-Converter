# Currency-Converter
A non-real time currency converter made to convert a few country currencies 


package Game.org;

import java.awt.*;
import java.awt.event.*;

import javax.swing.*;

public class Converter extends JFrame {

	private JPanel main;
	private JComboBox to, from;
	private JTextField input, output;
	private JLabel labt, labf, amount, rate;
	String selected;
	private String[] Country = {"Canada","Nigeria", "Euro", "USA", "UK"};
	Double[] C_rate = {0.00, 153.42, 0.71, 0.77, 0.49};
	Double[] N_rate = {0.0067, 0.00,0.0046,0.0050,0.0032};
	Double[] E_rate = {1.40, 215.52, 0.00, 1.08, 0.69};
	Double[] US_rate = {1.30,199.00,0.92,0.00,0.64};
	Double[] UK_rate = {2.02,310.50,1.44, 1.56, 0.00};
	double b_rate = 0.0000;
	int tindex;
	
	public Converter(){
		
		super("Currency Converter");
		
		this.setLayout(new FlowLayout());
		//initialize the panel that holds the main content
		this.getContentPane().setBackground(Color.darkGray);
		main = new JPanel();
		main.setLayout(new GridLayout(2,4,-8,10));
		selected = "Canada"; //default value
		tindex = 0; //default value
		
		labt = new JLabel("From:");
		main.add(labt);
		
		from = new JComboBox(Country);
		main.add(from);
		
		
		from.addItemListener(new ItemListener(){
		
			/*retrieve the information the user selected*/ 
			public void itemStateChanged(ItemEvent v){
			selected = (String)from.getSelectedItem();
			//output.setText("" + selected);
			}
			
		});
		
		
		//add the panel onto the frame
		labf = new JLabel("    To:");
		main.add(labf);
		
		to = new JComboBox(Country);
		main.add(to);
		
		amount= new JLabel("Amount:");
		main.add(amount);
		
		input = new JTextField(7);
		main.add(input);
		
		rate = new JLabel("    Output:");
		main.add(rate);
		
		output = new JTextField(7);
		main.add(output);
		
		to.addItemListener(new ItemListener(){
			 
			public void itemStateChanged(ItemEvent v){
			tindex = (Integer)to.getSelectedIndex();
		//	output.setText("" + tindex);
			} /*end of event handler*/
			
		});
	
		
		
		
		
		input.addActionListener(new ActionListener(){
		 
		   public void actionPerformed(ActionEvent ev){
		 
			   
			   output.setText("==> " + selected);
			   
			 if(selected.equals("Canada"))
						b_rate = C_rate[tindex];
					else if(selected.equals("Nigeria"))
						b_rate = N_rate[tindex];
					else if(selected.equals("Euro"))
					    b_rate = E_rate[tindex];
					else if(selected.equals("USA"))
						b_rate = US_rate[tindex];
					else if(selected.equals("UK"))
						b_rate = UK_rate[tindex];
				 
			int value = Integer.parseInt(input.getText());
			
			if(value == 1)
			 output.setText(""  + b_rate);
			else{
			 double result = (value * b_rate);
			 output.setText(""  + result);
			}
			   
		   }
		   
		});
		
		add(main);
	}
	
}
