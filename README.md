package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.eventloop.opmode.OpMode;
import com.qualcomm.robotcore.hardware.DcMotor;

@TeleOp(name="Mon TeleOp avec Intake", group="Iterative Opmode")
public class TeleOptest extends OpMode {

    private DcMotor motorLeft = null;
    private DcMotor motorRight = null;
    private DcMotor frontLeft = null;
    private DcMotor frontRight = null;
    private DcMotor Intake = null;

    @Override
    public void init() {
        motorLeft = hardwareMap.get(DcMotor.class, "motorLeft");
        motorRight = hardwareMap.get(DcMotor.class, "motorRight");
        frontLeft = hardwareMap.get(DcMotor.class, "frontLeft");
        frontRight = hardwareMap.get(DcMotor.class, "frontRight");
        Intake = hardwareMap.get(DcMotor.class, "Intake");
    }

    @Override
    public void loop() {

        double speedForward = gamepad1.right_trigger / 2.0;
        double speedBackward = -gamepad1.left_trigger / 2.0;
        double drive = speedForward + speedBackward;
        double turn = gamepad1.right_stick_x;
        double turnLeft = drive + turn;
        double turnRight = drive - turn;


        motorLeft.setPower(turnLeft);
        motorRight.setPower(turnRight);

        frontLeft.setPower(turnLeft);
        frontRight.setPower(turnRight);


        if (gamepad1.a) {
            Intake.setPower(1.0);
        } else {
            Intake.setPower(0.0);
        }



    }
}
