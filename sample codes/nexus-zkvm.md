## sample 1


```

#![no_std]
#![no_main]

// Import the core library for no_std environment
extern crate core;

use core::panic::PanicInfo;

/// Computes the nth Fibonacci number using an array.
///
/// # Arguments
///
/// * `n` - The position in the Fibonacci sequence.
///
/// # Returns
///
/// * The nth Fibonacci number.
fn fib(n: u32) -> u32 {
    // Use an array to store intermediate Fibonacci numbers
    let mut fib_array = [0u32; 50]; // assuming n < 50 for this example
    fib_array[0] = 0;
    fib_array[1] = 1;

    for i in 2..=n as usize {
        fib_array[i] = fib_array[i - 1] + fib_array[i - 2];
    }

    fib_array[n as usize]
}

// Entry point
#[nexus_rt::main]
fn main() {
    let n = 7;
    let result = fib(n);
    // The 7th Fibonacci number is 13
    assert_eq!(result, 13);
}


```

## sample 2


```

#![no_std]
#![no_main]

extern crate core;

use core::panic::PanicInfo;

/// Computes the greatest common divisor (GCD) of two numbers using Euclid's algorithm.
///
/// # Arguments
///
/// * `a` - First number.
/// * `b` - Second number.
///
/// # Returns
///
/// * The GCD of `a` and `b`.
fn gcd(mut a: u32, mut b: u32) -> u32 {
    while b != 0 {
        let t = b;
        b = a % b;
        a = t;
    }
    a
}

// Mock function to represent output in a `no_std` environment.
fn print_result(result: u32) {
    // In a real `no_std` environment, this might write to a serial port or display.
    // Here we just define it for conceptual completeness.
    // Example: write to memory-mapped I/O address or use platform-specific mechanisms.
    unsafe {
        let output_ptr = 0x1000 as *mut u32;
        *output_ptr = result;
    }
}

// Entry point
#[nexus_rt::main]
fn main() {
    let a = 56;
    let b = 98;
    let result = gcd(a, b);
    print_result(result);
    // Check the result for demonstration purposes (GCD of 56 and 98 is 14)
    assert_eq!(result, 14);
}


```
