void timer1_init(void);
void portf_init(void);
void setup() {
  // put your setup code here, to run once:
  portf_init();
  timer1_init();
  volatile char *outf=0x31;
  *outf=0x00;
  while(1){

  }
}
void loop() {
  // put your main code here, to run repeatedly:
}
void portf_init(void){
  volatile char *dirf=0x30;
  *dirf=0x01;
}
void timer1_init(void){
  volatile char *TCCR1_A = 0x80;  // FOR SELECTING MODE
  volatile char *TCCR1_B = 0X81;  // FOR ANY PRESCALER
  volatile unsigned short *TCNT1_L  = 0X84;  // FOR STORING COUNTING VALUE
  volatile unsigned short *OCR1A_L  = 0X88;  // COMPARED VALUE STORED HERE
  volatile char *TIMSK_1 = 0X6f;  // FOR ENABLING THE INTRRUPT
  // FOR CTC MODE AND PRESCALER=256
  *TCCR1_A  = 0X00;
  *TCCR1_B  = 0X0C;
  *TCNT1_L  = 0x00;  // COUNTING VALUE STARTS FROM 0
  *OCR1A_L  = 60000;  // GIVING COMPARED VALUE
  *TIMSK_1  = 0X02;  // Output Compare A Match Interrupt Enable
}
ISR(TIMER1_COMPA_vect) {
  volatile char *outf=0x31;    
  *outf=*outf^0x01;
}
