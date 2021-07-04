module fibonacci(input clk,
                 input reset,
                 input[7:0] nth_number,
                 output[19:0] fibonacci_number
                );

    reg[19:0] prev_value, cur_value;
    reg[7:0]  internal_counter;
    reg       number_ready;

    always@(posedge reset) begin
      prev_value <= 'd0;
      cur_value  <= 'd1;
      internal_counter <= 'd1;
    end

    always@(posedge clk) begin
      internal_counter <= internal_counter + 1;
      cur_value        <= cur_value + prev_value;
      prev_value       <= cur_value;
      if(internal_counter == (nth_number - 2))
        number_ready <= 1;
      else
        number_ready <= 0;
    end

    always@(number_ready) begin
      if(number_ready)
        $display("N = %d, Nth number is %d", nth_number, fibonacci_number);
    end

    assign fibonacci_number = cur_value;

endmodule
