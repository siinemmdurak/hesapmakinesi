# hesapmakinesi
enum Operation {
    Add(f64, f64),
    Subtract(f64, f64),
    Multiply(f64, f64),
    Divide(f64, f64),
}


fn calculate(op: Operation) -> f64 {
    match op {
        Operation::Add(a, b) => a + b,
        Operation::Subtract(a, b) => a - b,
        Operation::Multiply(a, b) => a * b,
        Operation::Divide(a, b) => a / b,
    }
}

fn main() {

    println!("Enter the first number:");
    let mut first_num = String::new();
    std::io::stdin().read_line(&mut first_num).expect("Failed to read input.");
    let first_num: f64 = first_num.trim().parse().expect("Invalid input. Please enter a number.");

    println!("Enter the operation (Add, Subtract, Multiply, Divide):");
    let mut operation = String::new();
    std::io::stdin().read_line(&mut operation).expect("Failed to read input.");
    let operation = operation.trim().to_lowercase();

    println!("Enter the second number:");
    let mut second_num = String::new();
    std::io::stdin().read_line(&mut second_num).expect("Failed to read input.");
    let second_num: f64 = second_num.trim().parse().expect("Invalid input. Please enter a number.");

    let op_enum = match operation.as_str() {
        "add" => Operation::Add(first_num, second_num),
        "subtract" => Operation::Subtract(first_num, second_num),
        "multiply" => Operation::Multiply(first_num, second_num),
        "divide" => Operation::Divide(first_num, second_num),
        _ => {
            println!("Invalid operation. Please choose from Add, Subtract, Multiply, or Divide.");
            return;
        }
    };

    let result = calculate(op_enum);
    println!("Result: {}", result);
}
