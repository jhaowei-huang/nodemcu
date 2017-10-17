pin = 3
baudrate = 115200 --baudrate used for communication

function setupRS485 () --setup
  gpio.mode(pin, gpio.OUTPUT)
  gpio.write(pin, gpio.LOW)
  uart.setup(0, baudrate, 8, 0, 1, 0) --UART 0, 9600 baud, 8 databits, 0 parity, 1 stopbit, no echo
end

uart.on("data", "\n",
  function(data)
    d = string.byte(data)
    if d == 10 then 
        return;
    end

    d = string.sub(data, 0, #data - 1)
    print("receive from uart:", d)
    
--    print("receive from uart:", string.sub(data, 0, #data - 1))
    if d=="quit" then
      uart.on("data") -- unregister callback function
    end
end, 0)

setupRS485()