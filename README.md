function fibonacciDivisibility(testCases, divisors)
    local fib = {0, 1} -- Inicializar la secuencia de Fibonacci con los primeros dos números
    local result = {} -- Almacenar los resultados de los casos de prueba
    
    -- Calcular los números de la secuencia de Fibonacci hasta que se alcance el índice más grande necesario
    while #fib < math.max(table.unpack(divisors)) do
        local nextNum = fib[#fib] + fib[#fib - 1] -- Calcular el siguiente número de Fibonacci
        table.insert(fib, nextNum) -- Agregarlo a la secuencia
    end
    
    -- Comprobar si cada número de la secuencia es divisible por los divisores dados
    for _, divisor in ipairs(divisors) do
        local indices = {} -- Almacenar los índices de los números divisibles
        
        -- Iterar sobre la secuencia y encontrar los índices de los números divisibles
        for i, num in ipairs(fib) do
            if num % divisor == 0 then
                table.insert(indices, i) -- Agregar el índice a la lista
            end
        end
        
        table.insert(result, table.concat(indices, " ")) -- Agregar los índices al resultado como una cadena separada por espacios
    end
    
    return result -- Devolver el resultado de los casos de prueba
end

-- Ejemplo de uso
local input = {
    2,
    {233328, 433156}
}

local testCases = input[1]
local divisors = input[2]

local output = fibonacciDivisibility(testCases, divisors)

-- Imprimir el resultado
for _, indices in ipairs(output) do
    print(indices)
end
