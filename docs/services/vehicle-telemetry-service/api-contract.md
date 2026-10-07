# Vehicle Telemetry API Contract

## Base URL

/api/v1

## POST /telemetry

Receives vehicle telemetry.

### Request

```json
{
  "telemetryId": "uuid",
  "vehicleId": "uuid",
  "timestamp": "2026-08-10T21:00:00Z",
  "rpm": 842,
  "speed": 0,
  "engineTemperature": 87.0,
  "batteryVoltage": 14.2,
  "fuelLevel": 41.7
}