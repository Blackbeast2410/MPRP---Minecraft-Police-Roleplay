# Testing

After significant changes:

1. Run the relevant Gradle build.
2. Fix compilation errors.
3. Start the affected runtime when practical.
4. Test the feature.
5. Test singleplayer behavior when relevant.
6. Test dedicated-server behavior when relevant.
7. Test networking when relevant.
8. Check persistence when relevant.
9. Check for obvious performance regressions.

Do not claim a test passed unless it was actually run.

Performance testing should eventually include scenarios such as:

- 1 police vehicle
- 5 police vehicles
- 20 police vehicles
- 50 police vehicles
- Multiple active lighting systems
- CAD traffic
- Multiple simultaneous pursuits
