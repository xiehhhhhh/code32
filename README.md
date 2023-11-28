# code32 
USE IEEE.std_logic_1164.ALL;
USE ieee.std_logic_unsigned.all;

ENTITY light IS
PORT (PUL,RST: IN std_logic;
LED: OUT std_logic_vector(5 downto 0)
);
END light;

ARCHITECTURE behav OF light IS
SIGNAL i:std_logic_vector(2 DOWNTO 0);

BEGIN

PROCESS(PUL,RST)
BEGIN
  if(RST='0') then
   LED<="000000";
   i<="000";
  elsif(PUL'event and PUL='1') then
    if(i=5) then
       i<="000";
      else 
           i<=i+'1';
     end if;
   case i is
      when "000"=>LED<="111110";
      when "001"=>LED<="111101";
      when "010"=>LED<="111011";
      when "011"=>LED<="110111";
      when "100"=>LED<="101111";
      when others=>LED<="011111";
      end case;
  end if;
 end process;
end behav;
