//D flip flop
module d_ff (
    input clk,
    input rst,
    input d_in,
    output reg q_out
);

always@(posedge clk) begin
    if(rst) begin
        q_out <= '0;
    end else begin
        q_out <= d_in;
    end
end
endmodule

//4bit SISO register
module register_4bit_siso #(
    parameter   SIZE=4
    ) (
    input x_in,
    input clk,
    input rst,
    output reg q_out[SIZE-1:0]
);

genvar i;
wire [SIZE-1:0]flop_in;
generate
    for(i=0; i<SIZE; i++) begin
        assign flop_in[i] = (i==0) ? x_in : q_out[(i-1)];
        d_ff d[SIZE-1:0] (
            .clk(clk),
            .rst(rst),
            .d_in(flop_in[i]),
            .q_out(q_out[i])
            );
    end
endgenerate

endmodule